# Personal Fork of [Cascade](https://github.com/andreasgrafen/cascade)

- [Catppuccin](https://github.com/catppuccin/catppuccin) Everything!
- Fonts used are all variants of [Iosevka](https://github.com/be5invis/Iosevka/).

All the source files are available in the [`chrome`](chrome/) folder. 

## How to use my config
<sub>From the upstream cascade repostiory.</sub>
1. Type `about:config` into your URL bar. Click on the **I accept the risk** button if you're shown a warning.
2. Seach for **`toolkit.legacyUserProfileCustomizations.stylesheets`** and set it to **`true`**.
3. Go to your profile folder:
  - Linux: `$HOME/.mozilla/firefox/######.default-release/`
  - MacOS: `Users/[USERNAME]/Library/Application Support/Firefox/Profiles/######.default-release`
  - Windows: `C:\Users\[USERNAME]\AppData\Roaming\Mozilla\Firefox\Profiles\######.default-release`
4. Copy the `chrome` folder into your profile and restart<sup>1)</sup> Firefox.

## The folders explained

The files are broken into 2 parts, `userChrome` and `userContent`.

### `userChrome`

These files influence the style of firefox itself.
It's mostly the same as original cascade, with some configuration options set.

- `userChrome.css`, `includes/` - Default cascade files, and configartion options.
- `integrations/` 
  - Catppuccin - Instead of this I am using the [official firefox theme](https://github.com/catppuccin/firefox). It provides more complete colouring for elements (such as the Downloads popup) in comparison to this. This is still included, as the variables are needed for the Side View integration.
  - Rosé Pine - Nice theme, should try it some time. Doesn't have many ports compared to catppuccin, though. Gonna leave this for now. Not used.
  - Tab Center Reborn - Doesn't work as I want it to. I know how to fix that, but it's too much effort. Not used.
  - Side View. - Is used, with some changes, that make it no longer minimal.

### `userContent`

The following files influence the style of web pages, as well as the developer tools window which is internally rendered as a seperate page.

- `userContent.css` - Entrypoint, sets the catppucccin colour palette as variables to be used later, as well as changes to the default browser styles.
- `content/about.css` - Sets the styles for firefox `about:` pages, such as the preferences and addons pages. (Tested on all pages on `about:about`)
- `content/devtools.css` - Sets the styles for the Inspector window as well as the Style Editor. Other pages may work, but I didn't style them as I'm too lazy for that. >:)
- `content/CodeMirror.css` - For any page using CodeMirror (devtools, codepen, etc.) force [Catppuccin](https://github.com/catppuccin/codemirror/) on it, regardless of what the developer specified.
- `content/hljs.css` - For any page using Highlight.js (mdBook, etc.) force [Catppuccin](https://github.com/catppuccin/highlightjs) on it, regardless of what the developer specified.
- `content/mdBook.css` - For any page using mdBook (documentation, usually for rust tools) force [Catppuccin](https://github.com/catppuccin/mdBook/) on it, regardless of what the developer specified.
