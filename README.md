# Code Notebook

**A lightweight, multi-language notebook in a single HTML file.**
Think Google Colab, minus the account, the install, and the extras you didn't ask for.

> Open `csharp-notebook.html` in your browser. That's the whole setup.

---

## Why does this exist?

Colab is great until it isn't: it's heavy, it wants you signed in, and it's really a Python tool.
I wanted something that opens instantly on a slow school PC and runs more than one language.

Yes, it's vibe-coded. It was a simple enough job that hand-building it made no sense.

## Features

- **18 languages**: Python, R, SQL, HTML/CSS, Java, Kotlin, C, C++, C#, JavaScript, TypeScript, Go, Rust, Scala, Dart, Ruby, PHP and Swift
- **Notebook cells**: code cells and text cells (basic Markdown), reorderable
- **Run one cell or Run all**
- **Language picker per cell**: the `+ Code` menu asks which language and drops in a Hello World template
- **Cell names**: every cell starts as `untitled1`, `untitled2`, ... and can be renamed
- **Cells as files**: cells in the same language can use each other like files in one folder (see below)
- **Console-style input**: the program's `input()` / `Console.ReadLine()` prompt appears right in the output
- **Syntax highlighting and autocomplete**, with code areas always in dark mode
- **Live HTML preview** for HTML cells
- **Save / Open** notebooks as JSON, or **Share** them as a link
- **Light and dark themes**

## Getting started

1. Download `csharp-notebook.html`.
2. Open it in any modern browser.
3. Click **Run all**, or the ▶ on a single cell.

No install, no build step, no account.

## How cells work

| | Behaviour |
|---|---|
| **C# cells** | Share variables and methods with each other. ▶ runs the cell plus the C# cells above it. |
| **HTML cells** | Rendered in a sandboxed preview, locally. |
| **Everything else** | Each cell runs on its own. |

### Using one cell from another

Give a cell a name (top right), then use it from another cell **in the same language**:

| Language | Example |
|---|---|
| Python | `import mymath` |
| JavaScript | `require("./mymath")` |
| TypeScript | `import { x } from "./mymath"` |
| Ruby | `require_relative "mymath"` |
| PHP | `require "mymath.php"` |
| R | `source("mymath.R")` |
| C / C++ | `#include "mymath.h"` |
| Java | use the class by name (the file is named after the class) |

Go, Rust, Kotlin, Scala, Swift, Dart and SQL don't support this.

## How it works (and what that means for privacy)

The page itself is plain HTML and JavaScript. To run your code it sends it to a
[Judge0](https://github.com/judge0/judge0) server, an open-source code-execution engine,
and shows the result. By default that's the free public instance at `ce.judge0.com`.

- **Your code is sent to that server** whenever you run a non-HTML cell. Nothing is sent to Google.
- **For full privacy**, host your own Judge0 and point the page at it under **Settings**.
- **HTML cells never leave your browser.**
- The page loads its editor libraries (CodeMirror, JSZip) from the cdnjs CDN, so it needs an internet connection. It is not an offline app.

## Limitations

- It doesn't host your files. Use **Save** (JSON) and **Open** to keep your work, or **Share** to make a link. Your browser also autosaves.
- The public Judge0 server is rate limited. If you see a 429 error, wait a moment or use your own server.
- Running a cell re-runs the cells it depends on, so random values or slow code repeat.
- Interactive input works by re-running the program with each line you type, so input-heavy programs are slower than a real terminal.
- Cell-to-cell references need a Judge0 server version 1.13 or newer.
- Some languages (Dart, for example) may be missing from the public server.

## Why it might work at school

- No account, no install, nothing to sign in to.
- The execution side is the same idea as the online compilers many classes already use:
  send code to a hosted runner and display the output.
- Everything else is plain HTML, which keeps it light on old hardware.

Check your school's rules before relying on it.

## Credits

- [Judge0](https://github.com/judge0/judge0) runs the code
- [CodeMirror 5](https://codemirror.net/5/) provides the editor
- [JSZip](https://stuk.github.io/jszip/) bundles cells together for cross-cell imports
