
```
------------- MY FILES ---------------
Used/ui-shared/src/searchPage/filtersv2/reducers/index.js
Used/ui-shared/src/searchPage/filtersv2/utils/index.js
Used/ui-shared/src/searchPage/reducers/index.js
Used/ui-shared/src/searchPage/scss/FilterV2.module.scss
common/ui/components/Navigation/Navigation.js
common/ui/components/Navigation/NavigationBody.js
common/ui/components/Navigation/NavigationDrawer.js
common/ui/components/Navigation/NavigationPopup.js
common/ui/ozone/components/BudgetFilter/BudgetFilter.js
common/ui/ozone/components/BudgetFilter/index.js
common/ui/ozone/components/ColorFilter/ColorFilter.js
common/ui/ozone/components/RheostatPillInput/index.js
common/ui/ozone/components/index.js
common/utility/LoadableComponentsRenderFunctions.cs
common/utility/ReactServer.cs
```


```
------------ STEPS ----------------------
other commit hash (from where you want to cherry pick):
a822224b46a4910f9e01d59ba714fadf1b7278d1

develop latest hash (latest branch where changes does not exists):
9725b06270c1e124da0a313ed19cf7c9ced30860

# shows the diff of file names
git diff a822224b46a4910f9e01d59ba714fadf1b7278d1 9725b06270c1e124da0a313ed19cf7c9ced30860 --name-only

# shows the diff of filenames that match certain path
git diff a822224b46a4910f9e01d59ba714fadf1b7278d1 9725b06270c1e124da0a313ed19cf7c9ced30860 --name-only | grep "^common/ui/ozone"


```

6952586aee4a9e156dfee1cb5bc82ff7f408ed7b


#git-magic
how to actually get diff of files starting with certain file name prefix like: `common/ui/ozone`

1. create a new branch out of develop (just to be on safe side)
2. `git checkout --patch a822224b46a4910f9e01d59ba714fadf1b7278d1 -- common/ui/ozone`




