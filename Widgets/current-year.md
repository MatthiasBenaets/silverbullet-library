#widget

Returns an `<a>` tag linking to the current year.
This function:
- Strips the curly braces to get the correct path
- Removes the path to display just the year
- Applies custom styling
- Add attributes for smooth navigations
  - class: `wiki-link`
  - data-ref: same link as the `href`

```space-lua
function currentYear(text)
  local strip = string.gsub(text, "[{}]", "")
  local trim = string.match(strip, "/([^/]*)$")
  return widget.html(
    dom.a {
      class = "wiki-link",
      style = "color: DodgerBlue; font-weight: bold; font-size: 24px;",
      href = strip,
      ["data-ref"] = strip,
      trim
    }
  )
end
```

Example usage:
${currentYear(tostring(query[[
  from index.tag "page"
  where string.match(name, "Work/Todo/" .. os.date("%Y"))
  select name
]]))}