# README

Dieses Projekt enthält ein Beispielprojekt für das Erstellen Research Papern
und das Exportieren in Word.

## Allgemeines

Das gesamte R Project kann über `Code` -> `Download ZIP` heruntergeladen werden. Damit
die Verweise auf die Dateien auch direkt funktioniert, muss RStudio immer über die `.Rproj` Datei geöffnet werden.

## Yaml Header

Ganz oben im Dokument befindet sich der Yaml Header. Hier werden die
Metadaten für das Dokument hinterlegt. Wichtig sind hier vor allem die Felder:

`title:` Titel des Dokuments in "" 
`author:` Autor des Dokuments in "" (i.d.R. eh anonymisiert und wird daher weggelassen)
`fig-title:` Was soll als Kürzel vor der Caption in Graphiken stehen? (z.B. Fig)
`fig-prefix:` Welches Kürzel soll in der Referenzierung von Graphiken genutzt werden? (z.B. Fig)
`title-delim:` Wie soll das Kürzel von dem Titel getrennt werden ("." oder ":")

Wichtig! Die Einzüge (Tabstopps) hier sind unfassbar wichtig! Wenn hier etwas nicht stimmt,
dann funktioniert der Export nicht!

## Word-Formatierung

In der Datei `custom-reference-doc.docx` sind die Formatvorlagen für das Ziel-
Word-Dokument hinterlegt. Wenn die allgemeine Formatierung geändert werden soll, 
dann werden die entsprechenden Formatvorlagen in dieser Datei angepasst.

## Überschriften

Überschriften werden über `#` für die erste Überschriftenebene, `##` für 
für die zweite Überschriftenebene, `###` für die dritte Überschriftenebene, usw.

## Zeilenumbrüche

Zeilenumbrüche werden über eine Leerzeile erreicht. Ein einfacher Umbruch im 
Text genügt nicht.

## R Code

R Code wird über sogenannte Chunks in das Quarto document eingefügt. Chunks 
werden über das Symbol c+ in der Leiste über den Editor eingefügt. In jedem 
Chunk werden zunächst die Eigenschaften mit `#| ` eingefügt. Die wichtigesten 
Eigenschaften sind:

`#| label:` Name des chunks (darf keine Sonder- oder Leerzeichen enthalten außer `-`)
`#| echo:` TRUE/FALSE, ob der Code im finalen Dokument angezeigt werden soll
`#| eval:` TRUE/FALSE, ob der Code ausgeführt werden soll
`#| warning:` TRUE/FALSE, ob Warnungen angezeigt werden sollen
`#| message:` TRUE/FALSE, ob Nachrichten angezeigt werden sollen

Wenn der Chunk die Erstellung einer Graphik enthält, werden zusätzlich folgende
Eigenschaften benötigt:

`#| fig.cap:` Bildunterschrift (caption)
`#| fig.align:` Ausrichtung der Graphik (left, center, right)
`#| out.width:` Breite der Graphik (z.B. "50%")
`#| dpi:` Auflösung der Graphik in DPI (z.B. 300)

## R Code im Text

R Code kann auch direkt im Text eingebunden werden. Dazu wird der Code in
einfach in Backticks `` ` `` eingeschlossen. Jeder in-line Code beginnt mit 
`r `. So lassen sich copy-paste Fehler vermeiden. Beispiel: Das aktuelle Jahr 
lässt sich beispielsweise über `r format(Sys.Date(), "%Y")` einfügen.

## Tabellen

Tabellen funktionieren hier nicht gut. Ich update das Dokument, wenn ich eine
gute Lösung gefunden habe.

## Referenzen

### Literatur

Literaturverweise werden über ein Literaturverzeichnis in der Datei 
`references.bib` verwaltet. Die Einträge können aus Zotero exportiert werden.
Zu jedem Eintrag gibt es einen eindeutigen Schlüssel (key), der im Text
verwendet wird, um auf den Eintrag zu verweisen. Der Verweis erfolgt über
`[@key]`. Wenn mehrere Einträge referenziert werden sollen, werden die Schlüssel
mit einem Semikolon getrennt: `[@key1; @key2]`. Wenn der Autor und das Jahr
getrennt angezeigt werden soll (Autor (Jahr)), kann das über `@key` erreicht 
werden.

Das Literaturverzeichnis wird dann über `::: {#refs}` in einer Zeile und `:::` 
in der nächsten Zeile eingefügt.
