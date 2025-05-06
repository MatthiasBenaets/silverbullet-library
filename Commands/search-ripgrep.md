#script

Search recursively through all files for keywords
Requires `ripgrep` on the host.
For Docker, run the command below or add it to the compose file like this:
```yaml
entrypoint: >
  /bin/bash -c "apt-get update && apt-get install -y ripgrep && /tini -- /docker-entrypoint.sh"
```

```space-lua
command.define {
  name = "Search Recursively",
  key = "Ctrl-s",
  run = function()
    -- get search term and search
    local term = editor.prompt()
    local selection = {}
    local results
    if term != null then
      results = rg(term)
    else return end

    if not results then
      editor.moveCursor(editor.getCursor()) -- for vim
      return editor.flashNotification("Nothing found", "warning")
    end
    
    -- create entry for each result
    for result in results do
      table.insert(selection, { 
        name = result.text,
        description = result.path,
        value = result
      })
    end
    
    -- selection modal
    local result = editor.filterBox("Select:", selection, "Found: " .. #results .. " entries")
    
    -- open file and navigate to position of match
    if result and result.value then
      local page, count = string.gsub(result.value.path, ".md", "")
      editor.navigate({ kind = "page", page = page })
      editor.moveCursorToLine(result.value.row, result.value.column, true)
    end
  end
}

function rg(term)
  -- ripgrep search term in all markdown files
  local args = {"-nb", "--type", "markdown", term}
  local found, results = pcall(shell.run, "rg", args)
  
  if found then
    local matches = string.split(results.stdout, "\n")
    local results = {}
    
    -- loop over all matches
    for match in matches do
      -- extract path, location in file and matched text
      local path, row, column, text = string.match(match, "^(.-):(.-):(.-):(.+)$")
      if (path ~= nil and row ~= nil and column ~= nil and text ~= nil) then
        table.insert(results, { path = path, row = row, column = column, text = text })
      end
    end
    
    return results
  else
    return
  end
end
```