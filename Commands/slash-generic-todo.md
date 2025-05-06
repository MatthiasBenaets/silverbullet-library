#slash

Old snippet to generate a TODO task.

```space-lua
  slashcommand.define {
    name = "generic-todo",
    run = function()
      editor.insertAtCursor([==[* [TODO] ]==])
    end
  }
```