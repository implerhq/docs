---
description: >-
  Guide on various building blocks of Impler, How they communicate and How
  Impler works?
---

# 🏗 Architecture

Impler is built upon scalable architecture to validate and process records of any size.

Separation of concern helps organizing code across various packages, libraries and apps. The idea is that app is divided into various parts, and each one is responsible for a spacific task.

Let's dive deep into building blocks of Impler.

## The mental model

<figure><img src="../.gitbook/assets/Screenshot from 2023-08-25 11-05-38.png" alt=""><figcaption><p>Impler Architectural Diagram</p></figcaption></figure>

### Widget

Widget is the main app where import happens. Widget provides UI to upload, map, validate and reivew data files. Widget gets embedded into iframe using `embed` script. It communicates with API to accomplish file processing work.

### Queue Manager

Queue manager handles processing data. Once user completes file import, the command gets passed to `Queue Manager` app to start processing data and sending it to application in chunks.

`Chunk` contains chunked data along with import information. More information on [using-webhook.md](../data-retrieval/using-webhook.md "mention")

### Authentication

API keys are used to authenticate APIs happening from import widget. Additionally developers can integrate Impler into their application by manually calling Impler API.

### SDKs

SDKs removes the need of managing import widget manually. In case of missing SDK developer can take reference of [iframe-embed.md](../widget/iframe-embed.md "mention")to embed widget into application.
