
> [!NOTE]
> See template example [Youtube with transcript](Template-guides/Youtube/YouTube-with-transcript.md)

## About

To extract content from **YouTube** videos using [[Resources/Obsidian-web-Clipper]], we can use a combination of **schema** and [selector variables](https://github.com/obsidianmd/obsidian-clipper?tab=readme-ov-file#selector-variables), to extract:
- video **upload date**, using `schema:@VideoObject:uploadDate`
- video **duration** (in seconds), using `schema:@VideoObject:duration`
- video **description**, using `{{schema:@VideoObject:description}}`
- video **transcript**, using `selectorHtml:.ytd-transcript-segment-list-renderer`

> [!TIP]
> [[Resources/Learning-about-CSS-selectors]]


## Example details

Let's use the "Obsidian October 2024 - Critique your plugin #1!" as an example:
Source video: https://www.youtube.com/watch?v=g2_XEDoPF4s

## Open transcript

To be able to extract the transcript, we also need to first open the transcript box, by pressing "more" and then "Show transcript"

![[Images/20241021093336-youtube-more.png]]

![[Images/20241021093412-youtube-show-transcript.png]]

Transcript should then load (if available), e.g.

![[Images/20241021093438-youtube-transcript.png]]
## Inspect the web page for elements to target

First, we can check what **page variables** [[Resources/Obsidian-web-Clipper]] is able to automatically "detect" for us, by selecting `...` in the extension.

If we scroll down, we see a lot of possible page variables. In this example, I've highlighted a few we will try to extract later.

![[Images/20241021093848-youtube-page-variables.png]]

> [!NOTE]
> Notice that `description` (text) and `uploadDate` (combined with **date filter**) can be used "as is", but that the `duration` (in seconds here) includes both a prefix and suffix, around the actual seconds part (PT**1039**S). Of course these prefixes and suffixes can have valid use cases (e.g. to indicate that it's time, and in seconds, etc.), but if we only want to extract the seconds part, meaning removing the prefix (PT) and suffix (S), we could use the **replace filter** to basically replace "something" with "something else", or in this case, replace "something" with "nothing". 
> 
> ```text
> {{schema:@VideoObject:duration|replace:"PT","","S",""}}
> ```


