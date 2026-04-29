#script

Create a new task for the to-do list.
By default, it creates a \[TODO\] with a unique tag.
The script will only run inside [[Work/Todo]] and a `TODO` tag is required in the frontmatter for this to work. 
It will auto-increment when creating a new task.

This is the normal variant. The `slashcommand` variant can be found at [[Custom/Commands/slash-todo]].

```space-lua
command.define {
  name = "Editor: Create Custom Task",
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

    -- prompt first, before making any changes
    local message = editor.prompt()
    if type(message) ~= "string" or message == "" then
      return
    end

    -- find the TODO value in frontmatter
    local content = editor.getText()
    local valueStr = tostring(value)
    local from, to = string.find(content, valueStr, 1, true)
    if not from then
      return editor.flashNotification("TODO index not found in content")
    end

    -- find cursor position (insertion point for new task)
    local cursor = string.find(content, "%* %[TODO%]") or
                   string.find(content, "%* %[DONE%]") or
                   #content + 1

    -- build the new task string
    local task = "* [TODO] #<" .. tostring(value + 1) .. "> " .. message .. "\n"
    if cursor == #content + 1 then
      task = "\n" .. task
    end

    -- adjust cursor for the frontmatter change offset
    -- replacing valueStr with (value+1) may shift positions if digit count changes
    local newValueStr = tostring(value + 1)
    local offset = #newValueStr - #valueStr

    -- dispatch both changes in one transaction
    editor.dispatch({
      changes = {
        { from = from - 1, to = to, insert = newValueStr },
        { from = cursor - 1 + offset, insert = task }
      }
    })

    -- move cursor to end of inserted task
    editor.moveCursor(cursor + offset + #task - 2)
  end
}
```