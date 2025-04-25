#style

Flash page title when saving.

```space-style
@keyframes saving {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.4;
  }
}

.sb-unsaved {
  animation: saving 2s infinite;
}

.sb-unsaved .cm-line {
  &::after {
    margin-left: 10px;
    position: relative;
    top: 0.1em;
    content: url('data:image/svg+xml,<svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="15" height="15" fill="rgb(187,194,207)" viewBox="0 0 24 24"> <path fill-rule="evenodd" d="M5 3a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V7.414A2 2 0 0 0 20.414 6L18 3.586A2 2 0 0 0 16.586 3H5Zm3 11a1 1 0 0 1 1-1h6a1 1 0 0 1 1 1v6H8v-6Zm1-7V5h6v2a1 1 0 0 1-1 1h-4a1 1 0 0 1-1-1Z" clip-rule="evenodd"/> <path fill-rule="evenodd" d="M14 17h-4v-2h4v2Z" clip-rule="evenodd"/> </svg>');
  }
}
```