This is where you configure SilverBullet to your liking. See [[^Library/Std/Config]] for a full list of configuration options.

```space-lua
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
      command = "Navigate: Home",
      description = "Go to the index page"
    },
    {
      icon = "folder",    
      command = "Navigate: Page Picker",
      description = "Open page"
    },
    {
      icon = "file-plus",    
      command = "Page: Create Page",
      description = "Create page"
    },
    -- {  
    --  icon = "git-merge",
    --  command = "Page: Create Subpage",
    --  description = "Create subpage"
    -- },
    {
      icon = "trash",
      command = "Page: Delete",
      description = "Delete page"    
    },
    {
      icon = "search",
      command = "Search Space",
      description = "Search for words in space"
    },
    {
      icon = "sidebar",
      command = "Tree View: Toggle",
      description = "Toggle Tree View"
    },
    {
      icon = "terminal",
      command = "Open Command Palette",
      description = "Run command"
    },
    -- {
    --  icon = "arrow-left", 
    --   command = "Navigate: Back in History",
    --   description = "Go to previous page"
    -- },
    -- {
    --   icon = "arrow-right",    
    --   command = "Navigate: Forward in History",
    --   description = "Go to next page"
    -- } 
  },
  shortcuts = {
    {
      command = "Task: Cycle State",
      key = "Ctrl-Enter",
    },
    {
      command = "Editor: Create Custom Task",
      slashCommand = "todo",
    }
  },
  vim = {
    unmap = {
      "<Space>",
      {
         key = "<C-c>",
        mode = "insert",
      },
    },
    map = {
      {
        map = "jj",
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
        map = "<Space>h",
        to = ":back<CR>",
        mode = "normal",
      },
      {
        map = "<Space>H",
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
    }
  }
}
```
