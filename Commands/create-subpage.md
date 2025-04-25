#script

Create a new subpage in the same directory
Page variant can be found here: [[Library/Custom/Commands/create-page]]

```space-lua
command.define {
  name = "Page: Create Subpage",
  run = function()
    local current = editor.getCurrentPage()
    local name = editor.prompt("Enter name of new subpage", current .. "/")
    if not name then return else editor.navigate(name) end
  end
}
```