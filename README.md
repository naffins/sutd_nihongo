# SUTD NihonGo Website Repository

Repository to host SUTD NihonGo's static website, using GitHub pages and Jekyll. Website design based on template "Editorial" by HTML5 UP (@ajlkn).

## Environment setup

### GitHub Pages

There is no need to setup an environment - GitHub automatically builds the static site and deploys it.

### Local

First, install Ruby - Jekyll runs on Ruby: [Ruby](https://www.ruby-lang.org/en/downloads/)

Next, on your command prompt (or Terminal), run

    gem install jekyll bundler

We will use bundler to manage Ruby dependencies (basically stuff that the website depends on). Jekyll generates the static site HTML files based on templates and provided content, so that you don't have to go around copying large chunks of HTML code when you just need to type 5 sentences for an event.

Next, run

    bundler update

This updates dependencies to the newest version.

Finally, run

    bundler exec jekyll serve

This runs the website on your local computer - you should see "Server address" which you can use to access a local version of this website.

## Housekeeping - Dependabot

Dependabot sometimes reports vulnerabilities for old Gem package versions. To rectify this, pull this repository, run

    bundler update

to update packages, then push the Gemfile. In most cases this should fix resolve any vulnerability alerts.

## Updating the website

ALWAYS TEST UPDATES BEFORE YOU PUSH AND DEPLOY TO THE SENPAI_UWU BRANCH ON GITHUB.

## Low-level explanation of repo structure (for those who want to get their hands dirty)

### _data

Contains constants for site operation.
- constants.yml contain constants to map between month number and month name.
- global_defaults.yml contain site-wide defaults such as logo and contact info.
- images.yml contain links to site images (other than logo). To be replaced with in-repo directory URL.

### _events

Contains contents of pages to be listed under Past Events section. Events are sorted and categorized in the Past Events page through JavaScript (see approximately lines 12-156). For this grouping/sorting, the pages' front matter is used.

### _includes

Contains template Liquid statements for quickly replicating code.
- date_formatting.html:
  For formatting a date period
  
  Arguments: start_
- test