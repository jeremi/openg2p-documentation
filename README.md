[![Netlify Status](https://api.netlify.com/api/v1/badges/855363c3-6ef3-4dbf-ae6c-440fa27d76ec/deploy-status)](https://app.netlify.com/sites/openg2pdoc/deploys)

# OpenG2P Documentations

Welcome to the repo for our documentation. This is the source for
[https://docs.openg2p.com/](https://docs.openg2p.com/).

Feel free to send us pull requests and file issues. Our docs are completely
opensource and we deeply appreciate contributions from our community!

> **NOTE** The theme and structure is based on the docker documentation repository

## Table of Contents

- [OpenG2P Documentations](#openg2p-documentations)
	- [Table of Contents](#table-of-contents)
	- [Providing feedback](#providing-feedback)
	- [Contributing](#contributing)
		- [Files not edited here](#files-not-edited-here)
		- [Overall doc improvements](#overall-doc-improvements)
	- [Staging the docs](#staging-the-docs)
	- [Important files](#important-files)
	- [Relative linking for GitHub viewing](#relative-linking-for-github-viewing)
		- [Testing changes and practical guidance](#testing-changes-and-practical-guidance)
		- [Per-page front-matter](#per-page-front-matter)
		- [Creating tabs](#creating-tabs)
		- [Running in-page Javascript](#running-in-page-javascript)
		- [Images](#images)


## Providing feedback

We really want your feedback, and we've made it easy. You can edit a page or
request changes in the right column of every page on
[docs.openg2p.com](https://docs.openg2p.com/).

**Only file issues about the documentation in this repository.** One way
to think about this is that you should file a bug here if your issue is that you
don't see something that should be in the docs, or you see something incorrect
or confusing in the docs.

- If your problem is a general question about how to configure or use OpenG2P,
  send us an email  [info@openg2p.org](mailto:info@openg2p.org) instead.

- If you have an idea for a new feature or behavior change in a specific aspect
  of OpenG2P, or have found a bug in part of OpenG2P, file that issue in
  the project's code repository.

## Contributing

We value your documentation contributions, and we want to make it as easy
as possible to work in this repository. One of the first things to decide is
which branch to base your work on. If you get confused, just ask and we will
help. If a reviewer realizes you have based your work on the wrong branch, we'll
let you know so that you can rebase it.

>**Note**: To contribute code to OpenG2P projects, see the
[Contribution guidelines](CONTRIBUTING.md).

### Files not edited here

Files and directories listed in the `path:` keys in
[`.NOT_EDITED_HERE.yaml`](.NOT_EDITED_HERE.yaml) are maintained in other
repositories and should not be edited in this one. Pull requests against these
files will be rejected. Make your edits to the files in the repository and path
in the `source:` key in the YAML file.

### Overall doc improvements

Most commits will be made against the `master` branch. This include:

- Conceptual and task-based information not specific to new features
- Restructuring / rewriting
- Doc bug fixing
- Typos and grammar errors

>Do you enjoy creating graphics? Good graphics are key to great documentation,
and we especially value contributions in this area.

## Staging the docs

You have three options:

1.  On your local machine, clone this repo and run our staging container:

    ```bash
    git clone --recursive https://github.com/openg2p/openg2p.github.io.git
    cd openg2p.github.io
    docker-compose up
    ```

    If you haven't got Docker Compose installed,
    [follow these installation instructions](https://docs.openg2p.com/compose/install/).

    The container runs in the background and incrementally rebuilds the site each
    time a file changes. You can keep your browser open to http://localhost:4000/
    and refresh to see your changes. The container runs in the foreground, but
    you can use `CTRL+C` to get the command prompt back. To stop the container,
    issue the following command:

    ```bash
    docker-compose down
    ```

2.  Install Jekyll and GitHub Pages on your local machine.

    a. Clone this repo by running:

       ```bash
       git clone --recursive https://github.com/openg2p/openg2p.github.io.git
       ```

    b. Install Ruby 2.3 or later as described in [Installing Ruby](https://www.ruby-lang.org/en/documentation/installation/).

    c. Install Bundler:

       ```bash
       gem install bundler
       ```

    d. If you use Ubuntu, install packages required for the Nokogiri HTML
       parser:

       ```bash
       sudo apt-get install ruby-dev zlib1g-dev liblzma-dev
       ```

    e. Install Jekyll and other required dependencies:

       ```bash
       bundle install
       ```

       >**Note**: You may need to install some packages manually.

    f. Change the directory to `openg2p.github.io`.

    g. Use the `jekyll serve` command to continuously build the HTML output.

    The `jekyll serve` process runs in the foreground, and starts a web server
    running on http://localhost:4000/ by default. To stop it, use `CTRL+C`.
    You can continue working in a second terminal and Jekyll will rebuild the
    website incrementally. Refresh the browser to preview your changes.

3. Build and run a docker image for your working branch.

   ```bash
   $ docker build -t docker build -t openg2p/docs:<branch_name> .
   $ docker run --rm -it -p 4000:4000 openg2p/docs:<branch_name>
    ```

   After the `docker run` command, copy the URL provided in the container build output in a browser,
   http://0.0.0.0:4000, and verify your changes.

## Read these docs offline

To read the docs offline, you can use either a standalone container.
To see all available tags, go to
[OpenG2P Hub](https://docs.openg2p.com/openg2p-hub/).

The following examples use the `latest` tag:

- Run a single container:

  ```bash
  docker run  -it -p 4000:4000 openg2p/docs:latest
  ```

You can now access the docs at port 4000 on your OpenG2P host.

## Important files

- `/_data/toc.yaml` defines the left-hand navigation for the docs
- `/js/menu.js` defines most of the docs-specific JS such as TOC generation and menu syncing
- `/css/style.scss` defines the docs-specific style rules
- `/_layouts/docs.html` is the HTML template file, which defines the header and footer, and includes all the JS/CSS that serves the docs content

## Relative linking for GitHub viewing

Feel free to link to `../foo.md` so that the docs are readable in GitHub, but keep in mind that Jekyll templating notation
`{% such as this %}` will render in raw text and not be processed. In general it's best to assume the docs are being read
directly on [https://docs.openg2p.com/](https://docs.openg2p.com/).

### Testing changes and practical guidance

If you want to test a style change, or if you want to see how to achieve a
particular outcome with Markdown, Bootstrap, JQuery, or something else, have
a look at `test.md` (which renders in the site at `/test/`).

### Per-page front-matter

The front-matter of a given page is in a section at the top of the Markdown
file that starts and ends with three hyphens. It includes YAML content. The
following keys are supported. The title, description, and keywords are required.

| Key                    | Required  | Description                             |
|------------------------|-----------|-----------------------------------------|
| title                  | yes       | The page title. This is added to the HTML output as a `<h1>` level header. |
| description            | yes       | A sentence that describes the page contents. This is added to the HTML metadata. |
| keywords               | yes       | A comma-separated list of keywords. These are added to the HTML metadata. |
| redirect_from          | no        | A YAML list of pages which should redirect to THIS page. At build time, each page listed here is created as a HTML stub containing a 302 redirect to this page. |
| notoc                  | no        | Either `true` or `false`. If `true`, no in-page TOC is generated for the HTML output of this page. Defaults to `false`. Appropriate for some landing pages that have no in-page headings.|
| toc_min                | no        | Ignored if `notoc` is set to `true`. The minimum heading level included in the in-page TOC. Defaults to `2`, to show `<h2>` headings as the minimum. |
| toc_max                | no        | Ignored if `notoc` is set to `false`. The maximum heading level included in the in-page TOC. Defaults to `3`, to show `<h3>` headings. Set to the same as `toc_min` to only show `toc_min` level of headings. |
| tree                   | no        | Either `true` or `false`. Set to `false` to disable the left-hand site-wide navigation for this page. Appropriate for some pages like the search page or the 404 page. |
| no_ratings             | no        | Either `true` or `false`. Set to `true` to disable the page-ratings applet for this page. Defaults to `false`. |
| skip_read_time             | no        | Set to `true` to disable the 'Estimated reading time' banner for this page. |

The following is an example of valid (but contrived) page metadata. The order of
the metadata elements in the front-matter is not important.

```liquid
---
description: Instructions for installing OpenG2P on Ubuntu
keywords: requirements, apt, installation, ubuntu, install, uninstall, upgrade, update
redirect_from:
- /erp/installation/ubuntulinux/
- /installation/ubuntulinux/
- /erp/installation/linux/ubuntulinux/
title: Get OpenG2P for Ubuntu
toc_min: 1
toc_max: 6
skip_read_time: true
no_ratings: true
---
```

### Creating tabs

The use of tabs, as on pages like [https://docs.openg2p.com/erp/api/](/erp/api/), requires
the use of HTML. The tabs use Bootstrap CSS/JS, so refer to those docs for more
advanced usage. For a basic horizontal tab set, copy/paste starting from this
code and implement from there. Keep an eye on those `href="#id"` and `id="id"`
references as you rename, add, and remove tabs.

```
<ul class="nav nav-tabs">
  <li class="active"><a data-toggle="tab" data-target="#tab1">TAB 1 HEADER</a></li>
  <li><a data-toggle="tab" data-target="#tab2">TAB 2 HEADER</a></li>
</ul>
<div class="tab-content">
  <div id="tab1" class="tab-pane fade in active">TAB 1 CONTENT</div>
  <div id="tab2" class="tab-pane fade">TAB 2 CONTENT</div>
</div>
```

For more info and a few more permutations, see `test.md`.

### Running in-page Javascript

If you need to run custom Javascript within a page, and it depends upon JQuery
or Bootstrap, make sure the `<script>` tags are at the very end of the page,
after all the content. Otherwise the script may try to run before JQuery and
Bootstrap JS are loaded.

> **Note**: In general, this is a bad idea.

### Images

Don't forget to remove images that are no longer used. Keep the images sorted
in the local `images/` directory, with names that naturally group related images
together in alphabetical order. For instance prefer `settings-file-share.png`
and `settings-proxies.png` to `file-share-settings.png` and
`proxies-settings.png`. You may also use numbers, especially in the case of a
sequence, e.g., `run-only-the-images-you-trust-1.svg`
`run-only-the-images-you-trust-2.png` `run-only-the-images-you-trust-3.png`.

When applicable, capture windows rather than rectangular regions. This
eliminates unpleasant background and saves the editors the need to crop.

On Mac, capture windows without shadows. To this end, once you pressed
`Command-Shift-4`, press Option while clicking on the window. To disable
shadows once for all, run:

```bash
$ defaults write com.apple.screencapture disable-shadow -bool TRUE
$ killall SystemUIServer  # restart it.
```

You can restore shadows later with `-bool FALSE`.

In order to keep the Git repository light, _please_ compress the images
(losslessly). On Mac you may use (ImageOptim)[https://imageoptim.com] for
instance. Be sure to compress the images *before* adding them to the
repository, doing it afterwards actually worsens the impact on the Git repo (but
still optimizes the bandwidth during browsing).
