# Styles
When switching themes, don’t forget to add/remove the `#disabled` tag.
Styles can quickly be enabled/disabled with the vim command:
- enable: `:%s/css space-style/space-style/g`
- disable: `:%s/space-style/css space-style/g`

## Active styles
${template.each(query[[
  from index.tag "space-style"
  select {name=ref}
]], templates.pageItem)}
## Disabled styles
${template.each(query[[
  from index.tag "disabled"
  select {name=ref}
]], templates.pageItem)}
