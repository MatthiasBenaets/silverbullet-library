#style

FiraCode supports ligatures:
<- -> == != >= <= => |- -| |> <| <> |-> <-| #! +++ --- ~~

```space-style
@font-face {
  font-family: 'Fira Code';
  src: url('https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Light.woff2') format('woff2'),
    url("woff/FiraCode-Light.woff") format("woff");
  font-weight: 300;
  font-style: normal;
}

@font-face {
  font-family: 'Fira Code';
  src: url('https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Regular.woff2') format('woff2'),
    url("woff/FiraCode-Regular.woff") format("woff");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: 'Fira Code';
  src: url('https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Medium.woff2') format('woff2'),
    url("woff/FiraCode-Medium.woff") format("woff");
  font-weight: 500;
  font-style: normal;
}

@font-face {
  font-family: 'Fira Code';
  src: url('https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-SemiBold.woff2') format('woff2'),
    url("woff/FiraCode-SemiBold.woff") format("woff");
  font-weight: 600;
  font-style: normal;
}

@font-face {
  font-family: 'Fira Code';
  src: url('https://cdnjs.cloudflare.com/ajax/libs/firacode/6.2.0/woff2/FiraCode-Bold.woff2') format('woff2'),
    url("woff/FiraCode-Bold.woff") format("woff");
  font-weight: 700;
  font-style: normal;
}

html {  
  --ui-font: "Fira Code", monospace;
}
```