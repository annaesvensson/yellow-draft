<p align="right"><a href="readme-de.md">Deutsch</a> &nbsp; <a href="readme.md">English</a> &nbsp; <a href="readme-sv.md">Svenska</a></p>

# Draft 0.9.1

Unterstützung für Entwurfsseiten.

<p align="center"><img src="screenshot.png" alt="Bildschirmfoto"></p>

## Wie man eine Erweiterung installiert

[ZIP-Datei herunterladen](https://github.com/annaesvensson/yellow-draft/archive/refs/heads/main.zip) und in dein `system/extensions`-Verzeichnis kopieren. [Weitere Informationen zu Erweiterungen](https://github.com/annaesvensson/yellow-update/tree/main/readme-de.md).

## Wie man eine Entwurfsseite macht

Ganz oben auf einer Seite kannst du `Status: draft` in den [Seiteneinstellungen](https://github.com/annaesvensson/yellow-core/tree/main/readme-de.md#einstellungen-seite) festlegen. Die Seite ist dann nicht mehr sichtbar. Du kannst die Seite weiterhin im [Webbrowser](https://github.com/annaesvensson/yellow-edit/tree/main/readme-de.md) und auf deinem [Computer](https://github.com/annaesvensson/yellow-core/tree/main/readme-de.md) bearbeiten.

## Wie man Entwurfsseiten wiederfindet

Du kannst die [Search-Erweiterung](https://github.com/annaesvensson/yellow-search/tree/main/readme-de.md) benutzen. Sobald du mit deinem Benutzerkonto angemeldet bist, kannst du nach `status:draft` suchen. Auf diese Weise kannst du alle Entwurfsseiten wiederfinden.

## Beispiele

Inhaltsdatei mit Draft-Status:

    ---
    Title: Beispielseite
    Status: draft
    ---
    Diese Seite ist auf deiner Webseite nicht sichtbar.

Inhaltsdatei mit Draft-Status fürs Wiki:

    ---
    Title: Wiki-Beispiel
    Layout: wiki
    Tag: Beispiel
    Status: draft
    ---
    Diese Seite ist in deinem Wiki nicht sichtbar.

Inhaltsdatei mit Draft-Status fürs Blog:

    ---
    Title: Blog-Beispiel
    Published: 2013-04-07
    Author: Datenstrom
    Layout: blog
    Tag: Beispiel
    Status: draft
    ---
    Diese Seite ist in deinem Blog nicht sichtbar.

Layoutdatei um alle Entwurfseiten anzuzeigen:

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

## Entwickler

Anna Svensson. [Hilfe finden](https://datenstrom.se/de/yellow/help/).
