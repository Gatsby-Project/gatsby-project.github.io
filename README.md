# How this Gatsby repo works and GitHub features

# GitHub

## Project Planning

## Code Management

## Security Scanning

## Secret Management
GitHub manages secrets within each repositories settings. You can easily add multiple secrets through the UI.

![alt text](https://miro.medium.com/max/700/1*CcuLAS9gezSz-6d6Lydw3Q.png)

For this repository, I only needed to use my own personal secret access token in order to have everything be deployed to GitHub Pages through the Actions pipeline.

![alt text](https://i.gyazo.com/cbd3c5f075582458f0c94bfcd4df8bad.png)
## Integrations
Integrations that have been implemented in this project was a simple 3rd party GitHub Action from the GitHub Marketplace that allows for a seamless deployment pipeline to publish my Gatsby web application to GitHub Pages.

Link: https://github.com/marketplace/actions/gatsby-publish

## MFA
This organization in GitHub as a whole requires it's members to have MFA enabled in order to join the organization. If they don't have MFA enabled on their own individual accounts, they cannot join. Also, if a member is already in the organization and does not have MFA enabled after the MFA rule is implemented in the organization, the member will be kicked from the organization.

## Analytics

# How this Gatsby project works

## Static Website Hosting through Github Pages
Static websites can be hosted on GitHub with GitHub Pages. You can host a website on GitHub's `github.io` domain or a custom domain.

This specific repository uses a 3rd party GitHub Action from the GitHub Marketplace called "Gatsby Publish", which allows for an easy integration into the GitHub Actions pipeline in order to publish to a domain in GitHub Pages.

### Main.yml
```
name: Gatsby Publish

on:
  push:
    branches:
      - develop

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
        with:
          ref: develop
      - uses: enriikke/gatsby-gh-pages-action@v2
        with:
          access-token: ${{ secrets.ACCESS_TOKEN }}
          deploy-branch: develop
```
This code uses an ubuntu image within the pipeline to run the specific Gatsby commands to deploy the web app. This script is configured by me to only be ran when their are changes made to the `develop` branch and not the `main` branch. This integration also requires that I use my personal GitHub `ACCESS_TOKEN` that I have defined securely in the repository.

To host your website code on GitHub Pages, it is as simple as going to the settings within your repository and selecting the "Pages" option in the menu. The repository does need to be public, but this will only make it public within the organization.

![alt text](https://docs.github.com/assets/images/help/repository/repo-actions-settings.png)

![alt text](https://docs.github.com/assets/images/help/pages/pages-tab.png)

Link to getting started with GitHub Pages: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
