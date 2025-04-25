#script

Create a new task for the to-do list.
By default, it creates a \[TODO\] with a unique tag.
The script will only run inside [[Work/Todo]] and a `TODO` tag is required in the frontmatter for this to work. 
It will auto-increment when creating a new task.

A shortcut is defined in [[CONFIG]]:
```lua
config.set {
  shortcuts = {
    {
      command = "Editor: Create Custom Task",
      slashCommand = "todo",
    }
  }
}
```

It’s also possible to just use `slashcommand.define` with an appropriate name.
But then it can’t be called via the Command Palette.
```space-lua
command.define {
  name = "Editor: Create Custom Task",
  run = function()
    -- only run when correct path is open
    local path = editor.getCurrentPage()
    if string.match(path, "Work/Todo/") then
      -- get metadata and content
      local meta = editor.getCurrentPageMeta()
      local value = meta.TODO
      local content = editor.getText()
  
      -- if todo metadata exists
      if value then
        -- update frontmatter meta to new value
        local from, to = string.find(content, value)
        editor.dispatch({
          changes = {
            from = from - 1,
            to = to,
            insert = tostring(value + 1),
          }
        })
  
        -- create task and move cursor to immediately type task
        local cursor = editor.getCursor()
        local task = "\n* [TODO] #<" .. tostring(value+1) .. "> "
        editor.dispatch({
          changes = {
            from = cursor,
            insert = task
          }
        })
        editor.moveCursor(cursor + string.len(task), true)
      else
        editor.flashNotification("TODO metadata not found")
      end
    else
      editor.flashNotification("Not in a Work/Todo/ file")
    end
  end
}
```
