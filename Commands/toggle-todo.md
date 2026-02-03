#script

Mark completed TODO tasks with date and time.
Checkbox variant can he found here: [[Custom/Commands/toggle-checkbox]]

```space-lua
local active = true;

if active then
  event.listen {
    -- listen for checkbox changes
    name = "task:stateChange";
    run = function(event)
      local path = editor.getCurrentPage()
      if string.match(path, "Work/Todo/") then
        -- get event data
        local data = event.data
        local from = data.from
        local to = data.to
        local text = data.text
        local newState = data.newState
        local state = string.match(text, "%[(.*?)%]")
        
        -- if checked
        if newState == "DONE" and state != "DONE" then
          -- complete task w/ datetime on a new line
          local now = os.date("%Y-%m-%d %a %H:%M")
          
          editor.dispatch({
            changes = { 
              from = to,
              insert = "\n  CLOSED: " .. now,
            },
          })
        elseif newState != "DONE" and state == "DONE" then
          -- if not done, clear checkbox and datetime
          local isCompleted = string.find(text, "\n  CLOSED:")
          local newText = string.gsub(text, "DONE", newState)
          local length = string.len(newText)
    
          if isCompleted then
          newText = string.gsub(newText, "\n  CLOSED:[^\n]*", "")
          end
          
          editor.dispatch({
            changes = {
              from = from,
              to = from + length,
              insert = newText,
            }
          })
        end
      end
    end
  }
end
```