# Emoji Explorer for Discord
A single-file web application for browsing and copying emojis, designed for Discord users. It runs entirely in the browser without any build steps or external dependencies besides web fonts and icons.

## Features
- Fetches live emoji data from the emoji-datasource API via jsDelivr.
- Automatically groups related emojis (gender variants, directional variants, etc.) into a single card to reduce clutter.
- Searchable and filterable by category, subcategory, and emoji version.
- Pagination limits the DOM to 250 cards at a time, reducing memory usage from over 1GB to roughly 70MB.
- Clicking an emoji opens a detail modal showing skin tones, related variants, Unicode data, and aliases.
- Click the emoji in the modal to copy the raw character, or click the code box to copy the Discord shortcode (e.g., `:smile:`).
- Includes a toggle to switch between a grouped grid and a flat grid.
- Dark mode interface with custom CSS variables.

## Usage
Download `EmojiExplorer.html` and open it in any modern web browser. There is no installation, server, or build process required.

## Technical Notes
- The application strips unused historical metadata from the fetched JSON to save memory and pre-computes search strings for faster filtering.
- Event delegation is used on the main container to handle clicks, avoiding the need to attach event listeners to hundreds of individual DOM nodes.
- Grouping relies on comparing the base Unicode codepoint of an emoji and applying a scoring system to pick the most generic representation (e.g., `person_running` over `man_running`) for the card.
- Includes a fallback to `document.execCommand('copy')` for browsers or environments where the Clipboard API is unavailable.

## Tech Stack
- HTML5
- CSS3
- Vanilla JavaScript (ES6+)
- Font Awesome (icons)
- Google Fonts (Nunito)

## License
MIT
