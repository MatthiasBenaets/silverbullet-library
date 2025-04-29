# Templates
More info:
- [[Library/Std/Template]]
- [[Library/Std/Slash Templates]]

Current Slash Templates:
${template.each(query[[
  from index.tag "meta/template/slash"
  where _.tag == "page"
]], templates.fullPageItem)}