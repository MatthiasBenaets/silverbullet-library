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
