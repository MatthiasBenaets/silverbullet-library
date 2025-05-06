#script

Create a new task for the to-do list.
By default, it creates a \[TODO\] with a unique tag.
The script will only run inside [[Work/Todo]] and a `TODO` tag is required in the frontmatter for this to work. 
It will auto-increment when creating a new task.

This is the normal variant. The `slashcommand` variant can be found at [[Library/Custom/Commands/slash-todo]].

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

    local cursor = string.find(content, "%* %[TODO%]") or
                   string.find(content, "%* %[DONE%]") or
                   #content + 1
       
    -- create task
    local message = editor.prompt()
    local task
    if type(message) == "string" and message ~= "" then
      task = "* [TODO] #<" .. tostring(value+1) .. "> " .. message .. "\n"
      if cursor == #content + 1 then
        task = "\n" .. task
      end
    else
      return editor.dispatch({
        changes = {
          from = from - 1,
          to = to,
          insert = tostring(value),
        }
      })
    end
    
    editor.dispatch({
      changes = {
        from = cursor - 1,
        insert = task
      }
    })
    
    -- move cursor to end of task
    editor.moveCursor(cursor + #task - 2)
  end
}
```