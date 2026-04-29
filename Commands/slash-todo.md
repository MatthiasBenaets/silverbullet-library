#slash

Create a new task for a to-do list.
By default, it creates a \[TODO\] with a unique tag.
The script will only run inside [[Work/Todo]] and a `TODO` tag is required in the frontmatter for this to work.
It will auto-increment when creating a new task.

This is the `slashcommand` variant. The normal command variant can be found at [[Custom/Commands/create-todo]].

```space-lua
slashcommand.define {
  name = "todo",
  description = "Create a TODO",
  run = function()
    -- check path
    local path = editor.getCurrentPage()
    if not string.match(path, "Work/Todo/") then
      return editor.flashNotification("Not in a Work/Todo/ file")
    end

    -- get metadata
    local meta = editor.getCurrentPageMeta()
    local value = meta.TODO
    if type(value) ~= "number" then
      return editor.flashNotification("TODO metadata not found")
    end

    -- re-fetch content after slash command is removed
    local content = editor.getText()
    local cursor = editor.getCursor()

    -- find TODO value in frontmatter
    local valueStr = tostring(value)
    local from, to = string.find(content, valueStr, 1, true)
    if not from then
      return editor.flashNotification("TODO index not found")
    end

    -- build task string
    local newValueStr = tostring(value + 1)
    local offset = #newValueStr - #valueStr
    local task = "* [TODO] #<" .. newValueStr .. "> "

    -- update frontmatter + insert task in one transaction
    editor.dispatch({
      changes = {
        { from = from - 1, to = to, insert = newValueStr },
        { from = cursor + offset, insert = task },
      }
    })

    -- move cursor to end of task prefix
    editor.moveCursor(cursor + offset + string.len(task), true)
  end
}
```
