---
tag: style
---
#style #active

# Base setup
## General
Inspiration: [doom-one](https://github.com/doomemacs/themes/blob/master/themes/doom-one-theme.el)

```space-style
/* Color scheme and variables */
:root {
  --bg: #282c34;
  --fg: #bbc2cf;
  --bg-alt: #21242b;
  --fg-alt: #5b6268;
  --base0: #1b2229;
  --base1: #1c1f24;
  --base2: #202328;
  --base3: #23271e;
  --base4: #3f444a;
  --base5: #5b6268;
  --base6: #73797e;
  --base7: #9ca0a4;
  --base8: #dfdfdf;
  --grey: var(--base4);
  --red: #ff6c6b;
  --orange: #da8548;
  --green: #98be65;
  --teal: #4db5bd;
  --yellow: #ecbe7b;
  --blue: #51afef;
  --dark-blue: #2257a0;
  --magenta: #c678dd;
  --violet: #a9a1e1;
  --cyan: #46d9ff;
  --dark-cyan: #5699af;
  --font-size: 18px;
  --editor-width: 960px;
  --line-height: 1.4em;
}

/* General appearance */
html {
  --ui-accent-color: var(--blue);
  --ui-accent-text-color: var(--magenta);
  --ui-accent-contrast-color: var(--bg);
  --root-color: var(--bg);
  --root-background-color: white;
  --meta-color: var(--red);
  --meta-subtle-color: var(--red);
  --subtle-color: var(--grey);
  --subtle-background-color: color-mix(in srgb, var(--grey) 10%, transparent);
  --editor-font: var(--ui-font);
  --editor-heading-color: var(--bg);
  --editor-wiki-link-page-color: var(--ui-accent-color);
  --editor-caret-color: var(--bg);
  --top-background-color: white;
  --action-button-hover-color: var(--ui-accent-color);
  --button-color: var(--action-button-color);
}

/* Dark mode */
html[data-theme=dark] {
  --ui-accent-color: var(--blue);
  --ui-accent-text-color: var(--magenta);
  --ui-accent-contrast-color: var(--fg);
  --root-color: var(--fg);
  --root-background-color: var(--bg);
  --editor-heading-color: var(--fg);
  --editor-caret-color: var(--fg);
  --top-background-color: var(--bg);
  --modal-color: var(--bg-fg);
  --modal-background-color: var(--bg-alt);
  --modal-help-background-color: var(--bg);
  --modal-selected-option-background-color: var(--ui-accent-color);
  --button-color: var(--action-button-color);
}

/* Font size */
.cm-editor {
  font-size: var(--font-size);
}

/* UI elements (cm-search) */
.cm-button {
  background-image: none !important;
  background-color: var(--violet) !important;
  border-radius: 3px !important;
  border: transparent !important;
  font-weight: bold !important;
  color: white !important;
}

.cm-textfield {
  border: 2px solid var(--violet) !important;
  border-radius: 3px;
  background-color: inherit !important;
}

html[data-theme=dark] {
  .cm-button {
    color: var(--bg) !important;
  }
}

/* Remove hidden query line */
.cm-line:has(+ .sb-lua-wrapper) {
  margin-top: calc(-0.5 * var(--line-height));
}
```

## Top
```space-style
/* Top bar appearance */
#sb-top {
  background-color: white;
  height: 24px;
}

/* Title and format */
#sb-top .main .inner {
  font-size: var(--font-size);
  padding: 0px;
}

#sb-top .main .inner div{
  color: var(--bg);
}

#sb-top .main #sb-current-page .cm-scroller {
  scrollbar-width: none;
}

/* Icons */
#sb-top .main .inner button, #sb-top .main .inner svg {
  height: var(--font-size);
  margin: auto;
}

.sb-actions button {
  padding: 0px;
  margin: 0px;
}

#sb-top .main .inner .sb-actions button:hover {
  color: var(--blue);
}

#sb-root:has(.sb-sync-error) .main .inner .sb-actions button:hover {
  color: white;
}

/* Sync Progress */
#sb-top .main .inner .sb-sync-progress .progress-wrapper {
  margin: 0px;
  background-color: transparent;
}

#sb-top .main .inner .sb-sync-progress .progress-bar {
  width: var(--font-size);
  height: var(--font-size);
  font-size: calc(var(--font-size) / 3);
  color: var(--magenta);
}

/* Offline */
#sb-top.sb-sync-error {
  background-color: color-mix(in srgb, var(--violet) 80%, transparent) !important;
}

/* Dark mode */
html[data-theme=dark] {
  #sb-top {
    background-color: var(--bg-alt);
  }
  
  #sb-top .main .inner div{
    color: var(--fg);
  }

  #sb-root:has(.sb-sync-error) .main .inner div {
    color: var(--bg) !important;
  }
  
  #sb-root:has(.sb-sync-error) .main .inner .sb-actions button {
    color: var(--bg);
  }
  
  #sb-top .main .inner .sb-actions button:hover {
    color: var(--green);
  }
  
  #sb-root:has(.sb-sync-error) .main .inner .sb-actions button:hover {
    color: var(--base5);
  }
}

/* Mobile toolbar */
@media only screen and (max-width: 600px) {
  #sb-top { opacity: 1 !important; }

  #sb-top .main .inner .sb-actions {
    background-color: var(--bg-alt);
  }

  #sb-top .main .inner .sb-actions button {
    color: var(--green);
  }

  #sb-top .main .inner .sb-actions button:hover {
    color: var(--teal);
  }

  #sb-top .sb-sync-progress:has(~ .hamburger) {
    margin-right: 3em;
  }

  #sb-root:has(.sb-sync-error) .main .inner .sb-actions button {
    color: var(--green) !important;
  }
}
```

## Frontmatter
```space-style
/* Background */
.sb-frontmatter {
  --editor-frontmatter-background-color: color-mix(in srgb, var(--blue) 8%, transparent) !important;
}

/* No Edit */
.sb-line-frontmatter-outside {
  padding-top: 5px !important;
  border-radius: 8px 8px 8px 8px;
}

/* No Edit: Content */
.sb-frontmatter.sb-line-frontmatter-outside:has(+ .sb-frontmatter) ~ .sb-frontmatter {
    display: none;
}

/* Edit: First line */
:not(.sb-frontmatter) + .sb-frontmatter:not(.sb-line-frontmatter-outside) {
  margin-top: 10px;
  border-radius: 8px 8px 0px 0px;
}

/* Edit: Content */
.sb-frontmatter-marker{
  color: var(--editor-code-info-color);
}
.sb-frontmatter:not(.sb-line-frontmatter-outside) {
  padding-left: 10px !important;
}

/* Edit: Last Line */
.sb-frontmatter:not(:has(+ .sb-frontmatter)) {
  margin-bottom: 10px;
  border-radius: 0px 0px 8px 8px;
}
```

## Tags
#style

```space-style
html {
  --editor-hashtag-color: var(--ui-accent-color) !important;
  --editor-hashtag-background-color: transparent !important;
  --editor-hashtag-border-color: var(--ui-accent-color) !important;
}
```

# Structural Hierarcy
## H2
### H3
#### H4
##### H5
###### H6
**bold**
*italic*
***italic bold***
~~Strikethrough~~

```space-style
/* Headers */
#sb-editor .sb-line-h1 {
  color: var(--blue);
}
#sb-editor .sb-line-h2 {
  color: var(--magenta);
}
#sb-editor .sb-line-h3 {
  color: var(--violet);
}
#sb-editor .sb-line-h4 {
  color: var(--green);
}
#sb-editor .sb-line-h5 {
  color: var(--yellow);
}
#sb-editor .sb-line-h6 {
  color: var(--orange);
}
/* Formatting character same color as text*/
#sb-editor .sb-meta{
  color: color-mix(in argb, var(--grey), 1% transparent) !important;
}
```

# Text Elements
## Highlight
This is a ==highlight==.
This is ==`code highlight`==.

```space-style
/* Normal highlight */
#sb-editor span.sb-highlight, .highlight {
  background-color: color-mix(in srgb, var(--yellow) 90%, transparent);
  color: var(--bg);
  padding: 0px 5px;
  border-radius: 5px;
}

/* Highlight for inline code */
#sb-editor .cm-content .cm-line > span > .sb-highlight.sb-code {
  background-color: color-mix(in srgb, var(--yellow) 60%, transparent) !important;
}
```

## Quotes
> Example quote!

```space-style
#sb-main .cm-editor .sb-blockquote-outside {
  border-left: 5px solid var(--magenta);
  text-indent: 1ch;
}
```

### Admonition
> **warning** Warning
> Example Warning

> **note** Note
> Example Note

> **tip** Tip
> Example Tip

> **important** Important
> Example Important

> **caution** Caution
> Example Caution

```space-style
/* Built-in admonition */
.sb-admonition[admonition="warning" i] {
  border-left: 5px solid var(--orange) !important;
  --admonition-color: var(--orange);
}

.sb-admonition[admonition="note" i] {
  border-left: 5px solid var(--blue) !important;
  --admonition-color: var(--blue);
}

/* Custom admonition */
.sb-admonition[admonition="tip" i] {
  border-left: 5px solid var(--green) !important;
  .sb-admonition-type * { display: none; }
  .sb-admonition-type::before { 
    width: var(--admonition-width) !important;
  }
  --admonition-icon: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24"> <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 9a3 3 0 0 1 3-3m-2 15h4m0-3c0-4.1 4-4.9 4-9A6 6 0 1 0 6 9c0 4 4 5 4 9h4Z"/></svg>'); 
  --admonition-color: var(--green);
}

.sb-admonition[admonition="important" i] {
  border-left: 5px solid var(--magenta) !important;
  .sb-admonition-type * { display: none; }
  .sb-admonition-type::before { 
    width: var(--admonition-width) !important;
  }
  --admonition-icon: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24"> <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 5.365V3m0 2.365a5.338 5.338 0 0 1 5.133 5.368v1.8c0 2.386 1.867 2.982 1.867 4.175 0 .593 0 1.292-.538 1.292H5.538C5 18 5 17.301 5 16.708c0-1.193 1.867-1.789 1.867-4.175v-1.8A5.338 5.338 0 0 1 12 5.365ZM8.733 18c.094.852.306 1.54.944 2.112a3.48 3.48 0 0 0 4.646 0c.638-.572 1.236-1.26 1.33-2.112h-6.92Z"/> </svg>'); 
  --admonition-color: var(--magenta);
}

.sb-admonition[admonition="caution" i] {
  border-left: 5px solid var(--red) !important;
  .sb-admonition-type * { display: none; }
  .sb-admonition-type::before { 
    width: var(--admonition-width) !important;
  }
  --admonition-icon: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24"> <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 13V8m0 8h.01M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"/> </svg>'); 
  --admonition-color: var(--red);
}
```

# Lists & Layout
## List
- bullet 1
  - sub-bullet 1
* bullet 2
1. number 1
2. number 2

```space-style
/* Unordered list */
#sb-editor .cm-list-bullet::after {
  color: var(--magenta);
}

/* Ordered list */
#sb-editor .sb-li-cursor .sb-meta {
  color: var(--magenta) !important;
}
```

## Checkbox
- [ ] unchecked
- [x] checked
- [DONE] done
- [TODO] todo

```space-style
/* No strikethrough */
#sb-main .cm-editor .cm-task-checked {
  text-decoration: none !important;
}

/* Task status text */
#sb-main .cm-editor .sb-task-state {
  color: var(--violet);
}

/* Checkbox appearance */
input[type="checkbox"] {
  appearance: none;
  -webkit-appearance: none;
  top: 2px;
  width: 15px !important;
  height: 15px !important;
  border: 2px solid var(--violet);
  border-radius: 4px;
  background-color: var(--white);
  /*background-color: var(--bg);*/
  cursor: pointer;
  position: relative;
}

/* Checkbox checked */
input[type="checkbox"]::before {
  content: "";
  position: absolute;
  top: 0px;
  left: 3px;
  width: 3px;
  height: 7px;
  border: solid white;
  /*border: solid var(--bg);*/
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  display: none;
}

input[type="checkbox"]:checked {
  background-color: var(--violet);
  border-color: var(--violet);
}

input[type="checkbox"]:checked::before {
  display: block;
}

/* Dark mode */
html[data-theme=dark] {
  input[type="checkbox"] {
    background-color: var(--bg);
  }
  
  input[type="checkbox"]::before {
    border-color: var(--bg);
    border-width: 0 2px 2px 0;
  }

  input[type="checkbox"]:checked {
    background-color: var(--violet);
    border-color: var(--violet);
  }
}
```

## Horizontal rule
Requires one empty line

---
***
```space-style
#sb-main .cm-editor .sb-line-hr {
  /*margin-top: var(--line-height);
  margin-bottom: 0em;*/
}
```

## Tables
| header 1 | header 2 | header 3|
| --- | --- | --- |
| info 1 | info 2 | info 3|
| info 4 | info 5 | info 6|

```space-style
html {
  --editor-table-head-background-color: transparent;
  --editor-table-head-color: color-mix(in srgb, var(--ui-accent-text-color) 70%, transparent);
  --editor-table-even-background-color: color-mix(in srgb, var(--ui-accent-color) 3%, transparent);
}

html[data-theme=dark] {
  --editor-table-head-background-color: transparent;
  --editor-table-head-color: var(--fg);
  --editor-table-even-background-color: transparent;
  /*--editor-table-even-background-color: color-mix(in srgb, var(--ui-accent-text-color) 3%, transparent);*/
}

/* Table appearance */
#sb-main .cm-editor table {
  border-collapse: collapse;
  margin-top: 10px;
  thead {
    font-size: 1em;
    line-height: 0.8em;
    background-color: color-mix(in srgb, var(--ui-accent-text-color) 15%, transparent);
    tr {
      font-weight: bold;
      opacity: 1;
      td {
        border-left: none;
        border-right: none;
      }
    }
  }
  td {
    border: 1px solid color-mix(in srgb, var(--fg) 30%, transparent);
    line-height: 0.8 rem;
    &:first-child {
      border-left: none;
    }
    &:last-child {
      border-right: none;
    }
  }
}
```

# Code
## Inline Code
This is `inline code`

```space-style
/* Inline code, highlight will overwrite background */
#sb-main .cm-editor .cm-line:not(.sb-line-fenced-code, .sb-line-code) > span > .sb-code {
  background-color: color-mix(in srgb, var(--root-color) 10%, transparent);
  padding: 0px 10px;
  border-radius: 5px;
}
```

## Code Block
### Triple tick
With code highlighting

```space-style
/* Rounding and padding */
.sb-line-fenced-code {
  padding: 0 15px !important;
}

.sb-line-fenced-code:first-of-type,
.sb-line-fenced-code:not(.sb-line-fenced-code + .sb-line-fenced-code) {
  border-top-left-radius: 0.5rem;
  border-top-right-radius: 0.5rem;
  padding-top: 10px !important;
}

.sb-line-fenced-code:last-of-type,
.sb-line-fenced-code:not(:has(+ .sb-line-fenced-code)) {
  border-bottom-left-radius: 0.5rem;
  border-bottom-right-radius: 0.5rem;
  padding-bottom: 10px !important;
}

.sb-line-code-outside {
  height: 5px !important;
}

/* Codeblock type */
#sb-main .cm-editor .sb-line-code-outside .sb-code-info {
  font-size: 70% !important;
  padding-right: 0px;
  padding-top: 5px;
}

/* Code highlighting */
.sb-meta {
  color: var(--blue);
}

.sb-keyword {
  color: var(--blue);
}

.sb-typeName {
  color: var(--blue);
}

.sb-variableName {
  color: var(--yellow);
}

.sb-number {
  color: var(--orange);
}

.sb-string {
  color: var(--green);
}

.sb-atom {
  color: var(--magenta);
}

.sb-operator {
  color: var(--blue);
}

.sb-comment {
  color: grey !important;
  /*font-style: italic !important;*/
}

html[data-theme=dark] {
  .sb-comment {
    color: var(--editor-code-comment-color) !important
  }
}
```

### Quadruple Space
No syntax highlighting. Requires one empty line.

    let test = 1
    console.log(test)

## Lua
### Directive
Custom plugs and Lua blocks.

```space-style
/* Remove decoration */
#sb-main .cm-editor .sb-lua-directive-block,
#sb-main .cm-editor .sb-lua-directive-inline,
#sb-main .cm-editor .sb-fenced-code-iframe iframe {
  border: none;
  padding: 0px;
  margin: 0px -1px;
}

/* Buttons*/
#sb-main .cm-editor .sb-lua-directive-block .button-bar {
  background-color: transparent;
}

/* Plugs and iframes */
#sb-main .cm-editor .sb-lua-directive-block .button-bar > button:hover {
  color: var(--action-button-hover-color);
}
```

### Button
Button widgets: ${widgets.button("Hello", function()
  editor.flashNotification "Hello"
end)}.

```space-style
/* Remove margin */
#sb-main .cm-editor .sb-lua-directive-inline:has(button) {
  margin: 0px !important;
}

/* Button appearance */
#sb-main .cm-editor .sb-lua-directive-inline button {
  padding: 0.5ch 2ch;
  background-color: var(--violet);
  border-color: transparent;
  border-radius: 5px;
  font-weight: bold;
  font-size: 70%;
  color: white;
  cursor: pointer;
  box-shadow: 0 4px 4px 0 rgba(0,0,0,0.1), 0 2px 2px 0 rgba(0,0,0,0.1);
}

/* Dark mode */
html[data-theme=dark] {
  #sb-main .cm-editor .sb-lua-directive-inline button {
    color: var(--bg);
  }
}
```

### Widgets
Custom Lua blocks at top or bottom of the page.

```space-style
/* Bottom spacing */
#sb-main .cm-editor .sb-lua-top-widget {
  margin-bottom: 10px;
}

/* Top spacing */
#sb-main .cm-editor .sb-lua-bottom-widget {
  margin-top: 10px;
}

/* Max height */
#sb-main .cm-editor .sb-lua-top-widget .content,
#sb-main .cm-editor .sb-lua-bottom-widget .content {
  max-height: 300px;
  scrollbar-width: none;
}

/* Title style */
#sb-main .cm-editor .sb-lua-top-widget h1,
#sb-main .cm-editor .sb-lua-bottom-widget h1 {
  color: var(--blue);
  font-size: 1.5rem;
  background-color: transparent;
}
```

### Query
Lua queries of (meta)data.

```space-style
/* Remove top spacing for block*/
.cm-line:has(.sb-lua-wrapper):has(.sb-lua-directive-block) {
  margin-top: -2ch;
}

/* ${} - will also use code highlighting*/
.sb-directive-mark {
  color: var(--red);
}
```

# Links & Navigation
## Links
General appearance
```space-style
html {
  --link-color: var(--magenta) !important;
  --link-missing-color: var(--red) !important;
}
```

Web URL: [silverbullet](https://silverbullet.md)
```space-style
a, .sb-link:not(.sb-meta, .sb-url) {
  color: var(--magenta);
}
```

Internal Links:
[[Library/Custom/Styles/theme|Existing link]]
[[Library/Custom/Styles/non-existant|None Existing Link]]
```space-style
/* Existing link */
.sb-wiki-link-page, a.wiki-link {
  color: var(--blue) !important;
  background-color: color-mix(in srgb, var(--blue) 2%, transparent) !important;
}

/* Non-existing link */
.sb-wiki-link-page-missing {
  color: var(--red) !important;
  background-color: color-mix(in srgb, var(--red) 2%, transparent) !important;
}
```

### Tooltip
When entering a link: \[\[\]\]

```space-style
/* Link tooltip */
#sb-editor .cm-editor .cm-tooltip {
  z-index: 99999 !important;
  border: solid 1px var(--violet);
  overflow: hidden;
}

/* Selection */
#sb-editor .cm-editor .cm-tooltip li[aria-selected] {
  background-color: var(--blue);
}

/* Rounding */
.cm-tooltip-below {
  border-radius: 0px 10px 10px 10px;;
}

.cm-tooltip-above {
  border-radius: 10px 10px 10px 0px;;
}
```

## Modals
Page picker, Command Palette, etc

```space-style
html {
  --modal-color: var(--bg);
  --modal-background-color: white;
  --modal-help-background-color: var(--fg);
  --modal-selected-option-background-color: var(--ui-accent-color);
  --modal-hint-background-color: var(--violet);
}

html[data-theme=dark] {
  --modal-color: var(--fg);
  --modal-background-color: var(--bg-alt);
  --modal-help-background-color: var(--bg);
  --modal-selected-option-background-color: var(--ui-accent-color);
  --modal-hint-background-color: var(--violet);

  .sb-modal-box .sb-selected-option .sb-description {
    color: var(--base8);
  } 
}
```

## TreeView
Hierarchically file browser

```space-style
/* Default file color */
.tree__label > span {
  background-color: transparent !important;
  border: none;
}

.tree__label > span[data-node-type="page"] {
  color: var(--magenta);
}

/* Folder color + folder icon */
.tree__node:has(.tree__subnodes:not(:empty)) > .tree__label > span[data-node-type="page"] {
  color: var(--blue);
  &::before {
    position: relative;
    top: 0.1em;
    content: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="rgb(81,175,239)" viewBox="0 0 24 24"> <path fill-rule="evenodd" d="M3 6a2 2 0 0 1 2-2h5.532a2 2 0 0 1 1.536.72l1.9 2.28H3V6Zm0 3v10a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V9H3Z" clip-rule="evenodd"/> </svg>');
  }
}

/* Opened folder icon */
.tree__node[open="true"]:has(.tree__subnodes:not(:empty)) > .tree__label > span {
  &::before {
    position: relative;
    top: 0.1em;
    content: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="rgb(81,175,239)" viewBox="0 0 24 24"> <path fill-rule="evenodd" d="M4 4a2 2 0 0 0-2 2v12a2 2 0 0 0 .087.586l2.977-7.937A1 1 0 0 1 6 10h12V9a2 2 0 0 0-2-2h-4.532l-1.9-2.28A2 2 0 0 0 8.032 4H4Zm2.693 8H6.5l-3 8H18l3-8H6.693Z" clip-rule="evenodd"/> </svg>');
  }
}

/* Folder (no file) color + folder icon */
.tree__label > span[data-node-type="folder"] {
  color: color-mix(in srgb, var(--blue) 60%, transparent);
  &::before {
    position: relative;
    top: 0.1em;
    content: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="rgb(81,175,239)" viewBox="0 0 24 24"> <path fill-rule="evenodd" d="M3 6a2 2 0 0 1 2-2h5.532a2 2 0 0 1 1.536.72l1.9 2.28H3V6Zm0 3v10a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V9H3Z" clip-rule="evenodd"/> </svg>');
  }
}

/* Opened page highlighting */
.tree__label:has(span[data-current-page="true"]) {
  background: linear-gradient(to right, 
    color-mix(in srgb, var(--violet) 40%, transparent) 0%, 
    transparent 100%);
  border-radius: 5px 0px 0px 5px;
}

/* Label background */
.tree__label > span[data-current-page="true"] {
  background-color: transparent !important;
}

/* TreeView background */
body:has(.treeview-root), .treeview-root, .treeview-root > .treeview-header {
  background-color: white !important;
}

/* Top bar */
.treeview-actions {
  background-color: white;
}

/* Top buttons */
.treeview-actions button {
  color: var(--green);
}

.treeview-actions button:hover {
  color: var(--teal);
}

.tree__collapse {
  color: var(--blue);
}

html[data-theme=dark] {
  .tree__label:has(span[data-current-page="true"]) {
    background: linear-gradient(to right, 
      color-mix(in srgb, var(--grey) 70%, transparent) 0%, 
      transparent 100%);
    border-radius: 5px 0px 0px 5px;
  }
  
  body:has(.treeview-root), .treeview-root, .treeview-root > .treeview-header {
    background-color: var(--bg-alt) !important;
  }
  
  .treeview-actions {
    background-color: var(--bg);
  }
}
```

# Miscellaneous
## Notification
Messages called with `editor.flashNotification`
Custom notification can be set up using `.sb-notification-<custom>`

```space-style
.sb-notification {
  color: var(--bg) !important;
  border-color: var(--bg) !important;
}

.sb-notification-info {
  background-color: color-mix(in srgb, var(--blue) 80%, transparent);
}

.sb-notification-warning {
  background-color: color-mix(in srgb, var(--red) 80%, transparent);
}
```

## Vim
Vim Mode

```space-style
/* Modeline appearance */
#sb-editor .cm-panels-bottom {
  background-color: white;
}

/* Modeline text */
#sb-editor .cm-panels-bottom .cm-vim-panel {
  color: var(--bg);
}

/* Commands */
#sb-editor .cm-panels-bottom .cm-vim-panel input {
  font-size: var(--font-size);
}

/* Cursor */
div:not(.cm-focused).cm-fat-cursor {
  color: color-contrast(var(--blue) vs white, black) !important;
  background-color: var(--blue) !important;
}

/* Message */
.cm-vim-message {
  color: var(--red) !important;
}

/* Dark mode */
html[data-theme=dark] {
  #sb-editor .cm-panels-bottom {
    background-color: var(--bg-alt);
  }
    
  #sb-editor .cm-panels-bottom .cm-vim-panel {
    color: var(--fg);
  }
}
```
