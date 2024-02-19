# ReactPagesAction
This Action will Build your React Project and deploy it to Github Pages

## Getting Started 🎉
1. In ``package.json`` add or edit ``"homepage": "https://**YourGithubName**.github.io/**YourRepoName**"``  

2. Create a Github Actions Workflow file and add this to it (and replace "YourGithubName" and "YourRepoName" with the names)
```yml
name: Build React App
on: [push]
permissions:
  contents: write # Permission for Action
jobs:
  build_react:
    runs-on: ubuntu-latest
    name: Build React
    steps:
    - uses: actions/checkout@v2
    - id: Build-React-App
      uses: BitDEVil2K16/ReactPagesAction@1.0.2
      with:
        username: 'YourGithubName'
        reponame: 'YourRepoName'
        token: ${{ secrets.GITHUB_TOKEN }} # Leave this line unchanged
```

3. Go to Settings -> Scroll down to GitHub Pages -> Select `gh-pages` as branch and `/` as directory 

## Options 🔧
|   Name   |            Description           |     Default    | Required |
|:--------:|:--------------------------------:|:--------------:|:--------:|
| username |           Your username          |        -       |     ✅    |
| reponame |       Your repository name       |        -       |     ✅    |
|   token  | Please leave this line unchanged |        -       |     ✅    |
| gitemail |         Git commit email         | CI@example.com |     ❌    |
|  gitname |          Git commit name         |       CI       |     ❌    |
|  gitmsg  |        Git commit message        |     deploy     |     ❌    |
|   cname  |           Custom domain          |        -       |     ❌    |
|  useyarn |         Use yarn to build        |      false     |     ❌    |


## Optional Custom Domain | cname
Change in ``package.json`` your Homepage and append cname in your yml.  
After token:
```yml
cname: 'yourcustomDomain.tdl'
```  

Full example with custom domain
```yml
name: Build React App
on: [push]
permissions:
  contents: write
jobs:
  build_react:
    runs-on: ubuntu-latest
    name: Build React
    steps:
    - uses: actions/checkout@v2
    - id: Build-React-App
      uses: BitDEVil2K16/ReactPagesAction@1.0.2
      with:
        username: 'YourGithubName'
        reponame: 'YourRepoName'
        token: ${{ secrets.GITHUB_TOKEN }} # Leave this line unchanged
        cname: 'example.com'
```
