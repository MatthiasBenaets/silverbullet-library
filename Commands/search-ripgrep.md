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
    -- open modal for search term
    local term = editor.prompt()
    -- find matches
    local results = rg(term)
    local selection = {}

    if results == 0 then
      return editor.flashNotification("Nothing found", "warning")
    end
    
    -- go over each find and create entry
    for result in results do
      table.insert(selection, { 
        name = result.text,
        description = result.path,
        value = result
      })
    end
    
    -- open model to list all entries and get user selection
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
  -- ripgrep for search term in all markdown files
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
    return 0 
  end
end
```