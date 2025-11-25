#meta

Script used for setting up the editor on initialization.

* Enable dark mode
* Enable vim mode

```space-lua
local function setSettings()
  clientStore.set("darkMode", true)
  clientStore.set("vimMode", true)
  system.reloadConfig()
end

event.listen {
  name = "editor:init",
  run = function()
    setSettings()
  end
}

event.listen {
  name = "editor:pageLoaded",
  run = function()
    setSettings()
  end
}
```
