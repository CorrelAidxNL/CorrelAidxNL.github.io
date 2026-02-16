# Framework

In this file we provide some background information about how this codebase generates the correaid.nl website.

## Repo Contents

In this list we just highlight the important sub-folders and files, rather than being comprehensive.
- components. Contains the code used to generate and style reusable website elements.
- docs. Destination for the final build of the website, 
  i.e. where GitHub picks up the built website for deployment via GitHub Pages.
  GitHub doesn't allow you to pick a custom name for this _deployment_ folder, 
  otherwise this folder would have a more meaningful and less confusing name.
- documentation. Where documentation (like this) at the level below the main repo readme live.
  The unfortunate forced naming convention from GitHub is why we have _docs_ and _documentation_.
- site. The folder containing the website content.
  When just updating the website, i.e. not doing genuine dev work, this is the only folder where you need to edit files.
  - _data. Various setting yml files.
  - _includes. HTML files defining website page elements.
  - _layouts. HTML files defining standard page templates.
  - _site. Where the local website _build_ lives when using the `jekyll serve` command to test changes locally.
  - collections. The main folder with the website content.
  Here the subfolders define various collections of different types of content that are used to build the website.
  - images. Where all images are saved.
  - _config.yml. The main website configuration file.
  - favicon.ico. CA NL logo that appears in browser tabs and URL (search) bar.

## How We Build The Website

For building the website, there are two basic commands. 
The `serve` command makes a build of the website and serves it so that it can be accessed via localhost.
All internal links are made to point to this localhost version of the website, so that you can test it locally.
The `build` command makes a build of the website which uses the actual website URL for internal links.
This build is thus suitable for deployment on the server (unlike the local test version _built_ via `serve`).

## Collections

When adding content to the website, typically you will only need to change content in the '/site/collections' folder,
whilst adding any new images to the 'site/images' folder.

Website pages are made in one of two ways. Either they are explicitly listed in the _pages_ collection 
or they are auto-generated based on the content of the other collections.
In the latter case, it should be straight-forward to add a new page by adding a new entry to the relevant collection.
Note that if you are wanting to make a genuinely new page in the _pages_ collection,
you need to also think about how the user will be able to navigate to that page, 
as it will not be linked to / added to the navigation bar automatically.
