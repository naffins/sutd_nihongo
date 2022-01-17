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

### Adding images

Place the desired image into /assets/imgs, ensuring that the image is not within any nested folder.

Please prepend "YYYY_MM_DD_" to image names according to when they were added, to avoid naming duplicates.

### Adding pages for past events

See /_events/20140319.html for an example.

Create an HTML file with the name "YYYYMMDD.html" in the /_events folder.

At the top of the file, insert front matter as shown below:

    ---
    id: "[YYYYMMDD]"
    title: "M[title of specific event page]"

    start_day: <D>D
    start_month: <M>M
    start_year: YYYY
    end_day: <D>D
    end_month: <M>M
    end_year: YYYY

    description: "[summary of event to be shown on past events page, and homepage if featured there]"
    cover_image: "[filename of photo to be shown on past events page, and homepage if featured there]"
    ---

Now you can add content below the front matter as if it were a normal HTML body, using paragraph and line break tags.

In some cases, you may want to use images. There are 2 ways to include images:

- As a single image - use

    {% include img_flex.html img_name="[image filename]" img_pos="fit" %}

- As a gallery - use

    {% include img_grid.html img_name_list="[image filename 1]&lt;, [image 2 filename]&lt;, [image 3 filename], ...>>" %}

## Low-level explanation of repo structure

### _data

Contains constants for site operation.
- constants.yml contain constants to map between month number and month name.
- global_defaults.yml contain site-wide defaults such as logo and contact info.

### _events

Contains contents of pages to be listed under Past Events section. Events are sorted and categorized in the Past Events page through JavaScript (see approximately lines 12-156). For this grouping/sorting, the pages' front matter is used.

### _includes

Contains template Liquid statements for quickly replicating code.
- date_formatting.html:
  For formatting a date period
  
  Arguments: start_day, start_month, start_year, end_day, end_month, end_year
- event_highlight.html:
  For displaying event highlights on the homepage
  
  Arguments: event - name of HTML file of event eg "20140329"
- img_flex.html:
  For showing images as a flex object (eg. to occupy the entire width of a page)

  Arguments: img_name, img_pos
- img_grid.html:
  For showing multiple images in a page as a gallery

  Arguments: img_name_list - string listing image names as ", " separated list
- img_src.html:
  For showing a single image
  Arguments: img_name

### _layouts

Contains default layouts for pages in the website.
- default.html: default layout for all pages in the website
- event.html: default layout for past events pages

### _site

Static site outputs (usually only apparent in local builds).

### imgs

Folder containing website images. To be optimized by ImgBot on GitHub.