<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Draft 0.8.16

Support for draft pages.

<p align="center"><img src="draft-screenshot.png?raw=true" alt="Screenshot"></p>

## How to make a draft page

Set `Status: draft` in the [page settings](https://github.com/datenstrom/yellow-extensions/tree/master/source/core#settings-page) at the top of a page. The page will no longer be visible. You can continue to edit the page in a [web browser](https://github.com/datenstrom/yellow-extensions/tree/master/source/edit) and on your [computer](https://github.com/datenstrom/yellow-extensions/tree/master/source/core).

## How to find draft pages

You can use the [search extension](https://github.com/datenstrom/yellow-extensions/tree/master/source/search). Once you're logged in with your user account, you can search with the `status:draft` filter for draft pages. This allows you to find all draft pages.

## Examples

Content file with draft status:

    ---
    Title: Example page
    Status: draft
    ---
    This page is not visible on your website.

Content file with draft status for the wiki:

    ---
    Title: Wiki example
    Layout: wiki
    Tag: Example
    Status: draft
    ---
    This page is not visible in your wiki.

Content file with draft status for the blog:

    ---
    Title: Blog example
    Published: 2013-04-07
    Author: Datenstrom
    Layout: blog
    Tag: Example
    Status: draft
    ---
    This page is not visible in your blog.

Layout file for showing all draft pages:

    <?php $this->yellow->layout("header") ?>
    <div class="content">
    <div class="main" role="main">
    <h1><?php echo $this->yellow->page->getHtml("titleContent") ?></h1>
    <?php $pages = $this->yellow->content->index(true, true)->filter("status", "draft") ?>
    <?php $this->yellow->page->setLastModified($pages->getModified()) ?>
    <ul>
    <?php foreach ($pages as $page): ?>
    <li><?php echo $page->getHtml("title") ?></li>
    <?php endforeach ?>
    </ul>
    </div>
    </div>
    <?php $this->yellow->layout("footer") ?>

## Installation

[Download extension](https://github.com/datenstrom/yellow-extensions/raw/master/downloads/draft.zip) and copy zip file into your `system/extensions` folder. Right click if you use Safari.

## Developer

Datenstrom. [Get help](https://datenstrom.se/yellow/help/).
