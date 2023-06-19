This is the error `cabal-install` generates for this project:

```
app/Main.hs:4:1: error:
    Could not load module ‘Language.LSP.Types’
    It is a member of the hidden package ‘lsp-types-1.6.0.0’.
    Perhaps you need to add ‘lsp-types’ to the build-depends in your .cabal file.
    It is a member of the hidden package ‘lsp-types-1.6.0.0’.
    Perhaps you need to add ‘lsp-types’ to the build-depends in your .cabal file.
    Use -v (or `:set -v` in ghci) to see a list of the files searched for.
  |
4 | import Language.LSP.Types
  | ^^^^^^^^^^^^^^^^^^^^^^^^^
Error: cabal: Failed to build exe:bad-cabal from bad-cabal-0.1.0.0.
```

First of all, for some reason there is some repetition in the error message.

Second, the error message is just bad. There is already `lsp-types` dependency listed in `.cabal` file. I would prefer in this scenario to not have any suggestions at all, but the other option would be to check during the error message generation to see whether the dependency is already there, and if it is, to display which version of the package it actually resolves to.
