https://github.com/nvm-sh/nvm/issues/1647

For NVM to work properly, you have to first uninstall your system node *and* your system npm. 

When you do `brew uninstall node`, it doesn't remove npm too. So you need to delete it manually:

```
rm /usr/local/bin/npm
```

:)
