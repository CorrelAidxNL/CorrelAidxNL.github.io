# Updating The Website

This file focuses on advice for on updating the website content, rather than genuine development work.
It assumes you are already familiar with the overall [framework](framework.md) and have a working local set-up.
See the [getting started](getting_started.md) document for installation instructions if this is still to be done.

## The Update Recipe

The basic recipe for making a change is as follows.

1. Make your changes on a dedicated branch of this repo, i.e. create a new branch and check it out locally.
2. Make small iterative changes testing them locally and committing each iteration separately.
3. When happy with all the changes, rebuild the website locally.
4. Selectively commit the changes made by the rebuild.
5. Push to the origin and make a pull request to master.
6. After merging, the new website version goes live and can be checked online.

### Testing Locally

To test changes to the website locally, you build and deploy on _localhost_. 
The cmd line command for this is `bundle exec jekyll serve`.
You need to execute this from the _site_ sub-folder rather than the root directory.
This command builds the website in the _\_site_ subfolder with your localhost as the root URL.
This ensures that internal links (e.g. for website navigation) keep you in the local test version.
The command prompt should give you a link with the server address so that you can check the website in the browser.
There is an auto-reload functionality providing live updating as you make changes.

### Rebuilding

If you are happy with the result locally, then you need to locally prepare for deployment on the server.
On the server, the _\docs_ folder will effectively be copy/pasted for deployment.
To make a deployment ready version of the website, 
rebuild the website with the command `bundle exec jekyll build -d ../docs`
This assumes you are still operating from within the _site_ subfolder 
and the '-d ../docs' part of the command sets the build destination to the _docs_ folder.
This command (with build NOT serve) takes the actual URL of our website (correlaid.nl) as the root URL.
We build in this docs folder, since that is the only subfolder GitHub Pages will accept for deployment.

Unfortunately the rebuild tends to make some unwanted _changes_ that we don't want to keep.
So before commiting you should go through and triage the changed files. 
- **Pagination**. When there are many items, Jekyll can split them across multiple pages (known as pagination).
  Sadly the Vonge template has implemented this in a way that only works properly when deploying via CloudCannon.
  On their [website](https://cloudcannon.com/templates/vonge/?ssg=jekyll), this issue has been acknowledged.
  As we are deploying via GitHub, this is a problem for us.
  Some of the links created for the pagination (to move between the various split pages) will be broken.
  This seems to happen when the pagination extends beyond two pages, which is why we didn't notice it at first.
  We haven't found a simple and proper solution to this, 
  possibly the codebase of the template needs some non-trivial changes. 
  A manual fix is to overwrite those links after making the build.
  For example, going to the _docs/blog/page/2/index.html_ file 
  and changing the href for _pagination__next_ from _"../../."_ to _"../../page/3/"_.
  This needs to be done for all links between pages 2 and greater, sadly.
  If no other change has been made to those pages, you can of course just roll them back.
- **Line endings / blank space**. Largely due to differences in local environments,
  the build often makes changes to files that have no impact on the website such as changed line endings 
  or adding/removing whitespace. 
  To avoid polluting the commit with such non-changes, please roll these back and do NOT commit them.
  Otherwise, you will make life hard for the reviewer of your pull request.
  Defining some standard git settings for this repo to solve this is on the to do list.

## Standard Content Updates

When just changing the content of the website and not doing development work, 
you will most likely only have to work with files in the _site/collections_ subfolder 
and add new images to the _site/images_ folder.
When adding image to serve as the main picture for a new entry, please make it square.

There are a few different collections that can be seen as three categories.
1. People / Posts / Projects.
   Each person, post or project listing has its own md file.
   Most pages and content are automatically generated from these collections.
   To make a new entry, simple make a new md file following the examples that are already there.
   Do not start filenames of new files with an underscore, as that is code for Jekyll to ignore it. 
2. Pages. 
   Certain pages are defined separately and explicitly.
   Editing an existing page should be straightforward,  
   but adding one requires more work to include links to it, e.g. in the navigation bar.
3. ~~Testimonials~~. Not in use.

## General Tips

Sometimes websites don't work as you expect, welcome to the world of front end development! Here are some tips.

- **Cache**. To avoid continuously downloading the same files, browsers make extensive use of caching.
  This means that a change to an existing file will not be immediately visible,
  since the browser will simply serve the old version of that file from the cache rather than downloading the new one.
  To see you changes when this happens, do a hard refresh of the page (e.g. ctrl-shirt-r for Firefox on Windows.)
- **Case Sensitivity**. Behaviour can be inconsistent with regards to the cases of filenames and their extensions.
  To avoid a gotcha with filenames, make sure the extensions are in lower case.
  This issue is particularly relevant if you are adding image files, i.e. check their extensions.
- **Build Locally**. Since we are using packages not supported by GitHub Pages, we cannot build on the server.
  Please check that the instructions in the section _Updating the Website_ have been fully followed.
  If you haven't copied the newly made website files to the _docs_ folder, then it will redeploy the old version.
  If you haven't added the empty _.nojekyll_ file to the root of the _docs_ folder it will fail to build on the server.
  If you haven't built the website using the build command (i.e. using serve instead), 
  then we will get references to localhost and broken links.
- **Auto Reload**. The serve commands support live updating of your locally served website when making changes.
  Note, however, that is common with most such functionalities, 
  there will be some types of changes that defeat the auto-reload.
  So when relying on that, do a manual reload (i.e. terminate and serve again) if something doesn't work as expected.
