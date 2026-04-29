#script

Mark completed TODO tasks with date and time.
Checkbox variant can he found here: [[Custom/Commands/toggle-checkbox]]

```space-lua
local active = true
if active then
  event.listen {
    name = "task:stateChange",
    run = function(event)
      local path = editor.getCurrentPage()
      if string.match(path, "Work/Todo/") then
        local data = event.data
        local from = data.from
        local to = data.to
        local text = data.text
        local newState = data.newState
        local state = string.match(text, "%[(.-) %]") or string.match(text, "%[(.-)%]")

        if newState == "DONE" and state ~= "DONE" then
          local now = os.date("%Y-%m-%d %a %H:%M")
          editor.dispatch({
            changes = {
              from = to,
              insert = "\n  CLOSED: " .. now,
            },
          })

        elseif newState ~= "DONE" and state == "DONE" then
          local newText = text

          -- strip CLOSED line first
          newText = string.gsub(newText, "\n  CLOSED:[^\n]*", "")

          -- then fix the checkbox state
          newText = string.gsub(newText, "%[DONE%]", "[" .. newState .. "]")

          editor.dispatch({
            changes = {
              from = from,
              to = from + string.len(text),
              insert = newText,
            }
          })
        end
      end
    end
  }
end
```