# Instructions for Updating this Fork

[Based on this article](https://medium.com/@denis.zhbankov/maintaining-a-fork-of-create-react-app-as-an-alternative-to-ejecting-c555e8eb2b63)

```sh
cd ./create-react-app

# Pull upstream changes into master branch
git checkout master
git pull upstream

# Rebase our custom branch onto the desired tag
git checkout custom-react-scripts
git rebase --onto v2.1.8 master
# Note: edit package.json to have an rc version, like 2.1.8-rc.1

# Publish package to NPM
cd packages/react-scripts
npm publish --access public

# Update package.json in main app, and test locally
# Once we confirm everything is working, we could update this package's version to drop the -rc.1, but that isn't really necessary

# Force push our rebased branch up to Github (careful, make sure it is all working first!)
cd ../..
git status
git push origin --force
```