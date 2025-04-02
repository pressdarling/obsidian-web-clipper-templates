
## About

To extract content from **GitHub Releases** using [[Resources/Obsidian-web-Clipper]], we can use [selector variables](https://github.com/obsidianmd/obsidian-clipper?tab=readme-ov-file#selector-variables), to extract only the **release information** content.

> [!TIP]
> [[Resources/Learning-about-CSS-selectors]]

## TLDR

Selectors we use in this (example) template

```text
{{selectorHtml:.markdown-body|markdown}}
```

## Example details

Let's use the release notes for Obsidian Web Clipper 0.9.3 as an example.
Source page: https://github.com/obsidianmd/obsidian-clipper/releases/tag/0.9.3

Rendering the page directly in the browser, usually results in something like:
![[Images/20241020125032-github-releases.png]]

In this example, we want to extract only the text from the 0.9.3 release notes, meaning content from both headings "New" and "Improved".

### Inspecting the web page for elements to target

To find the respective elements to extract (using selector variables), we can use the [developer tools](https://developer.chrome.com/docs/devtools/open) in the browser, then search for the relevant content, usually by pressing e.g. `Cmd + Option + I` (macOS), or `F12`. Another quick way to inspect the elements, is simply right clicking click the elements we want to use (selector or selectorHtml)

![[Images/20241020130646-github-releases-inspect.png]]

Notice that if we "hover" the "New" part in the developer tools, the browser dynamically highlights the parts we select in the developer tools.

![[Images/20241020130900-github-releases-h2.png]]

If we then hover over the `div` (one level up from `<h2>New<h2>`), we can see that this is the part we actually want to clip. In this case, it seems that the class selector `.markdown-body` can be used to extract the content we need (again, see [[Resources/Learning-about-CSS-selectors]] for a more deepdive on the different class selectors)

![[Images/20241020131050-github-releases-markdown-body.png]]


### Testing

Let's test...

In our clipper template, we include the selector we identified above, like this

```text
{{selectorHtml:.markdown-body|markdown}}
```

In short:

- `selectorHtml` to specify what element from the page we to extract
- `.markdown-body` to use the class we identified above
- `|markdown` to convert the HTML data (as we use `selectorHtml`) into Markdown

> [!NOTE]
> Note that we here use `selectorHtml`, as it sometimes result in better content clipping, especially for code blocks, and special formatting

![[Images/20241020132115-clipper-selectorHtml-markdown-body.png]]

Trying to use the clipper with the new template, it should result in something like below:

![[Images/20241020132715-github-releases-side-by-side.png]]