---
aliases: Youtube with Transcript
description:
publish: true
cover:
permalink: youtube/youtube-with-transcript
tags:
---

Related guide: [[Clipper-guides/Obsidian Web Clipper Template Guide for YouTube with transcript]]

This template should be able to extract:
- video **upload date**, using `schema:@VideoObject:uploadDate`
- video **duration** (in seconds), using `schema:@VideoObject:duration`
- video **description**, using `{{schema:@VideoObject:description}}`
- video **transcript**, using `selectorHtml:.ytd-transcript-segment-list-renderer`

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