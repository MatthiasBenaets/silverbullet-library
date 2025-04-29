#widget

Returns a clickable breadcrumbs menu at the top of the page.

```space-lua
local active = false
local home = "index"

function widgets.breadcrumbs()
  -- get path
  local path = editor.getCurrentPath()
  local crumbs = {}
  local current = ""

  if path ~= home then
    -- loop over each section of the path
    for part in string.gmatch(path, "[^/]+") do
        if current == "" then
            current = part
        else
            current = current .. "/" .. part
        end
        -- add link to breadcrumb list
        table.insert(crumbs, "[[" .. current .. "]]")
    end

    -- prepend home link
    table.insert(crumbs, 1, "[[" .. home .. "|Home]]")

    -- return rendered breadcrumb trail
    return widget.new {
      markdown = table.concat(crumbs, " > ")
    }
  else
    return -- no breadcrumbs on homepage
  end
end

if active then
  -- add widget to top of page
  event.listen {
    name = "hooks:renderTopWidgets",
    run = function()
      return widgets.breadcrumbs()
    end
  }
end
```
