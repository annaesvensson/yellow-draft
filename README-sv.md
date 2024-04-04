<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Draft 0.9.1

Stöd för draftsidor.

<p align="center"><img src="SCREENSHOT.png" alt="Skärmdump"></p>

## Hur man installerar ett tillägg

[Ladda ner ZIP-filen](https://github.com/annaesvensson/yellow-draft/archive/refs/heads/main.zip) och kopiera den till din `system/extensions` mapp. [Läs mer om tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md).

## Hur man skapar en draftsida 

Ställ in `Status: draft` i [sidinställningar](https://github.com/annaesvensson/yellow-core/tree/main/README-sv.md#inställningar-page) högst upp på en sida. Sidan kommer inte längre att visas. Du kan fortsätta att redigera sidan i [webbläsaren](https://github.com/annaesvensson/yellow-edit/tree/main/README-sv.md) och på din [dator](https://github.com/annaesvensson/yellow-core/tree/main/README-sv.md).

## Hur man hittar draftsidor

Du kan använda [search-tillägget](https://github.com/annaesvensson/yellow-search/tree/main/README-sv.md). När du är inloggad med ditt användarkonto kan du söka efter `status:draft`. På så sätt kan du hitta alla draftsidor igen.

## Exempel

Innehållsfil med draft-status:

    ---
    Title: Exempelsida
    Status: draft
    ---
    Den här sidan visas inte på din webbplats.

Innehållsfil med draft-status för wikin:

    ---
    Title: Wiki exempel
    Layout: wiki
    Tag: Exempel
    Status: draft
    ---
    Den här sidan visas inte i din wiki.

Innehållsfil med draft-status för bloggen:

    ---
    Title: Blogg exempel
    Published: 2013-04-07
    Author: Datenstrom
    Layout: blog
    Tag: Exempel
    Status: draft
    ---
    Den här sidan visas inte i din blogg.

Layoutfil för att visa alla draftsidor:

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

## Utvecklare

Anna Svensson. [Få hjälp](https://datenstrom.se/sv/yellow/help/).
