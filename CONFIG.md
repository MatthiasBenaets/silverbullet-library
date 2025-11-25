This is where you configure SilverBullet to your liking. See [[^Library/Std/Config]] for a full list of configuration options.

This is a duplicate of [[CONFIG]].

```lua
config.set {
  plugs = {
    -- Add your plugs here (https://silverbullet.md/Plugs)
    -- Then run the `Plugs: Update` command to update them[
    "github:joekrill/silverbullet-treeview/treeview.plug.js",
    "github:silverbulletmd/silverbullet-mermaid/mermaid.plug.js"
  },
  actionButtons = {
    {
      icon = "home",
      description = "Go to the index page",
      run = function()
        editor.invokeCommand("Navigate: Home")
      end
    },
    {
      icon = "folder",    
      description = "Open page",
      run = function()
        editor.invokeCommand("Navigate: Page Picker")
      end
    },
    {
      icon = "file-plus",    
      description = "Create page",
      run = function()
        editor.invokeCommand("Page: Create Page")
      end
    },
    -- {  
    --  icon = "git-merge",
    --  description = "Create subpage",
    --  run = function()
    --    editor.invokeCommand("Page: Create Subpage")
    --  end
    -- },
    {
      icon = "trash",
      description = "Delete page",
      run = function()
        editor.invokeCommand("Page: Delete")
      end
    },
    {
      icon = "search",
      description = "Search for words in space",
      run = function()
        editor.invokeCommand("Search Space")
      end
    },
    {
      icon = "sidebar",
      description = "Toggle Tree View",
      run = function()
        editor.invokeCommand("Tree View: Toggle")
      end
    },
    {
      icon = "terminal",
      description = "Run command",
      run = function()
        editor.invokeCommand("Open Command Palette")
      end
    },
    -- {
    --   icon = "arrow-left",
    --   description = "Go to previous page",
    --   run = function()
    --     editor.invokeCommand("Navigate: Back in History")
    --   end
    -- },
    -- {
    --   icon = "arrow-right",    
    --   description = "Go to next page",
    --   run = function()
    --     editor.invokeCommand("Navigate: Forward in History")
    --   end
    -- } 
  },
  shortcuts = {
    {
      command = "Task: Cycle State",
      key = "Ctrl-Enter",
    },
  },
  vim = {
    unmap = {
      "<Space>",
    },
    map = {
      {
        map = "jk",
        to = "<Esc>",
        mode = "insert",
      },
    },
    noremap = {
      {
        map = "<",
        to = "<gv",
        mode = "visual",
      },
      {
        map = ">",
        to = ">gv",
        mode = "visual",
      },
      {
        map = "<Space>ff",
        to = ":findfile<CR>",
        mode = "normal",
      },
      {
        map = "<Space>rc",
        to = ":runcommand<CR>",
        mode = "normal",
      },
      {
        map = "<Space>fg",
        to = ":findgrep<CR>",
      },
      {
        map = "<Space>it",
        to = ":cyclestate<CR>",
        mode = "normal",
      },
      {
        map = "<Space><Left>",
        to = ":back<CR>",
        mode = "normal",
      },
      {
        map = "<Space><Right>",
        to = ":forward<CR>",
        mode = "normal",
      },
      {
        map = "<Space>e",
        to= ":toggletree<CR>",
      },
    },
    commands = {
      {
        command = "Navigate: Page Picker",
        ex = "findfile",
      },
      {
        command = "Open Command Palette",
        ex = "runcommand",
      },
      {
        command = "Search Recursively",
        ex = "findgrep",
      },
      {
        command = "Task: Cycle State",
        ex = "cyclestate",
      },
      {
        command = "Navigate: Back in History",
        ex = "back",
      },
      {
        command = "Navigate: Forward in History",
        ex = "forward",
      },
      {
        command = "Tree View: Toggle",
        ex = "toggletree",
      },
    }
  },
  treeview = {
    position = "bhs",
    size = 0.5,
    dragAndDrop = {
      enabled = true,
      confirmOnRename = true
    },
    exclusions = {
      {
        type = "regex",
        rule="^(?:Library|Repositories|CONTAINER_BOOT).*$",
      },
    }
  }
}
```
