#style

Improved TreeView styling.

- Correctly resizes depending on screen width
- Moves menu to side in landscape mode and to bottom in portrait mode.
- Resizes font depending on viewport for better readability
- Required in [[Library/Custom/CONFIG]]:
```lua
config.set {
  treeview = {
    position = "bhs",
  }
}
```

```space-style
html {
  --treeview-phone-height: 25vh;
  --treeview-tablet-width: 25vw;
  --treeview-tablet-height: 100vh;
  --treeview-desktop-width: 20vw; 
}

.sb-bhs {
  height: var(--treeview-phone-height);
}

.tree__label > span {
  font-size: calc(14px + 0.5vh); 
}

@media (min-width: 960px) {
  #sb-root:has(.sb-bhs) #sb-main,
  #sb-root:has(.sb-bhs) #sb-top {
    margin-left: var(--treeview-tablet-width);
  }

  .sb-bhs {
    position: fixed;
    left: 0;
    height: var(--treeview-tablet-height);
    width: var(--treeview-tablet-width);
    border-right: 1px solid var(--top-border-color);
    border-top: none;
  }
}

@media (min-width: 1440px) {
  #sb-root:has(.sb-bhs) #sb-main,
  #sb-root:has(.sb-bhs) #sb-top {
    margin-left: var(--treeview-desktop-width);
  }

  .sb-bhs {
    width: var(--treeview-desktop-width);
  }
}
```