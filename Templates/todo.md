#template

Used to correctly list the aggregated tasks in [[Work/Todo]].

```space-lua
templates.todoItem = template.new([==[
* [${state}] ${name}
]==])
```

For example:
${template.each(query[[
  from index.tag "task"
  where page:startsWith("Work/Todo/") and parent == nil
  select { name = text, state = state}
  order by page desc, pos
  limit 10
]], templates.todoItem)}
