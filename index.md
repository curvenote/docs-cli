---
title: Curvenote CLI
description: ""
date: 2021-08-25T20:06:05.379Z
author:
  - "@rowanc1"
name: index
oxa: oxa:EplL6AlILV3RGEDPzj5U/qO37OgRXvWSbykWGvaDR
---

# Curvenote CLI

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/IaFX0NQNRnPdm5tvByQ2.6","pinned":false}

`curvenote` is a library and a command line interface (CLI) that provides modern tooling for technical writing and reproducible science. Our [mission](https://curvenote.com/why) is to help in transitioning scientific communication out of static documents and promote more connections between how researchers work, and how they share that work.

Critical to that mission is providing tools that:

1. are accessible to programmers and non-programmers alike;
2. allow creation of interactive, computationally driven online documents;
3. allow you to reuse components of documents across various resources; and
4. export to traditional formats, like PDF, PPT and Word to support your existing workflows.

The CLI and all dependencies made by Curvenote are open-source (MIT License) and we contribute to upstream projects where we can (e.g. our founders are members of [Executable Books](https://executablebooks.org/en/latest/team.html)). The Curvenote CLI provides local content transformations, with an early focus on providing 100s of [LaTeX templates](https://github.com/curvenote/templates) for various scientific journals. The library also provides a connection to sync your local documents with [curvenote.com](https://curvenote.com/) to aid in collaborative writing, especially in bridging the gap between those who can use Markdown, Git, and a Shell and those of us who are not programmers. We think this is especially important for writing workflows, where the collaboration and communication process is often quite different than a Git-driven approach.

```{important}
**⭐ Roadmap ⭐**

We are releasing a version of `curvenote` on Jan 20, 2022 that is an early preview mostly focused on export of static documents (PDF and Word) from Curvenote. Our general roadmap over the coming months is:

1. support JupyterBook as a first class interoperable format;
2. provide additional LaTeX and Word templates that support multi-article content (e.g. thesis, large reports);
3. support two-way data-sync to Markdown and other supported formats; and
4. support new interactive formats for HTML publishing.
```

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/K4wNaODT2DBRm1NwVVNY.4","pinned":false}

## **Installing** `curvenote`

Curvenote is currently available through Node, you will have to [install Node](https://nodejs.org/en/) and make sure you have `npm` (Node package manager) installed. If you have installed Jupyter, you likely also have Node installed on your computer, so the following command may just work! 🙂

```shell
npm install -g curvenote
```

This will install `curvenote` globally (`-g`) on your system and add a link to the main CLI tool. To see if things worked, try checking the version with:

```shell
curvenote -v
```

Which should print the current version of the package. If all is good, you can type `curvenote` again in your terminal and it will list the help with all of the options available to you.

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/YqsgIMcfgtnP9cyOzlGZ.1","pinned":false}

### Dependencies for LaTeX and PDF

If you are exporting to LaTeX with an open-source template specified (see all [templates](https://github.com/curvenote/templates)) or if you are creating a PDF you will need to install the [jtex](https://pypi.org/project/jtex/) python package to be installed and available on the user's `PATH`. With [Python 3.7](https://www.python.org/downloads/) or greater installed, install `jtex` via pip:

```shell
  python -m pip install jtex
```

For LaTeX PDF builds you will also require a version of LaTeX to be installed.

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/MSQinWImjrfaa13213mK.1","pinned":false}

## **Usage as a package**

`curvenote` is a node module, and you can use it to chain together other types of workflows that are not possible through the CLI.

```typescript
import { Session, MyUser } from 'curvenote';

const session = new Session(token);
const user = await new MyUser(session).get();
console.log(user.data.username);
```

## Developing

For the [curvenote](https://github.com/curvenote/curvenotejs) library on GitHub, `git clone` and you can install the dependencies and then create a local copy of the library with the `yarn dev:cli` command.

```shell
git clone git@github.com:curvenote/curvenotejs.git
cd curvenotejs
yarn install
yarn dev:cli
```

This will create a local copy of `curvenote` for use on the command line.

