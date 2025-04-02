---
aliases: Sample template guide
description: Enter your template description here
publish: true
cover:
permalink: meta/sample-template-guide
tags: Meta
---

%% Delete all markdown comments when done %%

%% Add your image. It should be in `.webp` format. ![IMAGE ALT TEXT](IMAGE HERE) %%

## Description

%% What does it do? Edit this in your PR %%
%% Need a completed example? See [YouTube with transcript](Template-guides/Youtube/YouTube-with-transcript.md) %%

%% Add your image. It should be in `.webp` format. %%

![IMAGE ALT TEXT](IMAGE HERE)


## 

### Related resources
%% Add a link to the .json download. Erase if there is none. %%
**Download the `.json`**: `[sample-templayte.json](sample-template.json)`

You can also copy the codeblock below to paste into Obsidian Clipper with the following steps.

1. Copy the codeblock below
2. Go to Obsidian Clipper.
3. Go to Clipper settings
4. Select **New template**.
5. Select the **Import** button
6. Paste the `.json` content into the Json template area.
7. Select import. 

## Template codeblock

%% Paste your .json contents in the json codeblock below %%
```json
{
  "schemaVersion": "0.1.0",
  "name": "YouTube with transcript",
  "behavior": "create",
  "noteContentFormat": "## About\n\ntype:: #type/video/youtube/new\n\n![{{title}}]({{url}})\n\n## Description\n\n{{schema:@VideoObject:description}}\n\n## Notes\n\nYT=\n\n\n## Transcript\n\n{{selectorHtml:.ytd-transcript-segment-list-renderer|replace:\"&nbsp;\":\" \"|join|markdown}}",
  "properties": [
    {
      "name": "created",
      "value": "{{time|date:\\\"YYYY-MM-DDTHH:mm:ssZ\\\"}}",
      "type": "date"
    },
    {
      "name": "reviewed",
      "value": "",
      "type": "text"
    },
    {
      "name": "url",
      "value": "{{url}}",
      "type": "text"
    },
    {
      "name": "title",
      "value": "{{title}}",
      "type": "text"
    },
    {
      "name": "channel",
      "value": "{{schema:@VideoObject:author}}",
      "type": "text"
    },
    {
      "name": "related",
      "value": "[[Videos]]",
      "type": "text"
    },
    {
      "name": "published",
      "value": "{{schema:@VideoObject:uploadDate|date:\\\"YYYY-MM-DD\\\"}}",
      "type": "date"
    },
    {
      "name": "duration",
      "value": "{{schema:@VideoObject:duration|replace:\\\"PT\\\",\\\"\\\",\\\"S\\\",\\\"\\\"}}",
      "type": "text"
    },
    {
      "name": "watched",
      "value": "",
      "type": "text"
    }
  ],
  "triggers": [],
  "noteNameFormat": "{{schema:@VideoObject:uploadDate|date:\"YYYY-MM-DD\"}} VIDEO {{schema:@VideoObject:author}} - {{title|safe_name}}",
  "path": ""
}
```