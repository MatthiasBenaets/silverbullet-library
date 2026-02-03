#script

Mark checked checkboxes with date and time.
TODO variant can he found here: [[Custom/Commands/toggle-todo]]

```space-lua
local active = false;

if active then
  event.listen {
    -- listen for checkbox changes
    name = "task:stateChange";
    run = function(event)
      -- get event data
      local data = event.data
      local from = data.from
      local to = data.to
      local text = data.text
      local newState = data.newState
  
      -- if checked
      if newState == "x" then
        -- complete task w/ datetime on a new line
        local now = os.date("%Y-%m-%d %a %H:%M")
        
        editor.dispatch({
          changes = { 
            from = to,
            insert = "\n  CLOSED: " .. now,
          },
        })
      elseif newState == " " then
        -- if unchecked, clear checkbox and datetime
        local newText = string.gsub(text, "x", newState)
        newText = string.gsub(newText, "\n  CLOSED:[^\n]*", "")
        
        editor.dispatch({
          changes = {
            from = from,
            to = to,
            insert = newText,
          }
        })
      end
    end
  }
end
```