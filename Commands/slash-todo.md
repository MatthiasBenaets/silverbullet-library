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

    -- update frontmatter
    local content = editor.getText()
    local from, to = string.find(content, value)
    if from and to then
      editor.dispatch({
        changes = {
          from = from - 1,
          to = to,
          insert = tostring(value + 1),
        }
      })
    else
      return editor.flashNotification("TODO index not found")
    end

    -- create task
    local cursor = editor.getCursor()
    local task = "* [TODO] #<" .. tostring(value+1) .. "> "
    editor.dispatch({
      changes = {
        from = cursor,
        insert = task
      }
    })

    -- move cursor to write task
    editor.moveCursor(cursor + string.len(task), true)
  end
}
```
