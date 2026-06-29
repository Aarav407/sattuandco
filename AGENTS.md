# sattuandco

## Cursor Cloud specific instructions

### What this is
This repo is a single self-contained static web page: the file `sattu` (no extension) is a complete HTML document for the "Sattu & Co." storefront (product grid, add-to-basket side panel with live total, and a WhatsApp checkout link). All CSS, JS, and images (base64 data URIs) are inlined in that one file. There is no package manager, build step, backend, or automated test suite, so there are no dependencies to install.

### Running it (dev)
- The file is named `sattu`, not `sattu.html`, so a default static server serves it as a download. To render it in a browser, serve it with an explicit `text/html` content type.
- A simple way is a small Python (`python3`, preinstalled) `http.server` handler that reads `/workspace/sattu` and returns it with `Content-Type: text/html`, listening on a port (e.g. 8000). Then open `http://localhost:8000/`.
- Do not rename or modify `sattu` just to make serving easier; map the path in the server instead.

### Testing
- No lint, build, or automated tests exist. Validate changes by serving the page and exercising the UI manually: add products (`Add` buttons), open the basket (header button), adjust quantities, and confirm the `#totalAmt` footer total updates. The `Order on WhatsApp` button opens an external `wa.me` link (uses `WA` phone constant) — do not rely on it in headless tests.
