#script

Create a new page in the same subdirectory.
Subpage variant can be found here: [[Library/Custom/Commands/create-subpage]]

```space-lua
command.define {
  name = "Page: Create Page",
  run = function()
    local current = editor.getCurrentPage()
    local path = string.gsub(current, "/*[^/]+$", "")
    if path ~= "" then path = path .. "/" end
    local name = editor.prompt("Enter name of new page", path)
    if not name then return else editor.navigate(name) end
  end
}