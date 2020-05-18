# TransferWise Public Widgets
TransferWise Public Widgets provides an easy way to embed a TransferWise widget in your HTML.

Available widgets:
- **Comparison**: A comparison table, with selectors for the route and amount.
- **Comparison Table**: A static comparison table for a fixed route and amount.

## Usage
There are two steps to adding this widget to any page.

### Step 1
Add an `<a>` tag to your HTML in the position where you would like the widget to render.

e.g:
```html
  <a class="tw-comparison"
    href="https://transferwise.com/gb/compare/?sendAmount=1000&sourceCurrency=GBP&targetCurrency=INR"
    data-lang="es"
  >
    The true cost of sending GBP to INR
  </a>
```

The `class` should vary depending on the widget you would like to render:
- **Comparison**: `class="tw-comparison"`
- **Comparison Table**: `class="tw-comparison-table"`

**Mandatory href query parameters**

Specify in the `href` query parameters the **sendAmount**, **sourceCurrency** and **targetCurrency** to be compared.

**Optional parameters**

- `data-lang`: `string` ISO 639-1. Default `en`
- `data-source-country`: `string`  ISO 3166-1 alpha-3. Filter results by source country. i.e the origin country from where a user may want to send money from.
- `data-provider-country`: `string` ISO 3166-1 alpha-2. Filter by provider country. i.e the country which the provider belongs to (e.g Natwest - GB, ANZ - AU).
                                    This property is also useful for only showing national banks, rather than "global" providers (like Western Union, Moneygram etc)
- `data-max-visible-providers`: `number` by default shows 3 providers and the rest are hidden under [Show more providers]() link.
- `data-expand-disclaimer`: `boolean` will render the table with the disclaimer already opened and scrolls the element into the visible area of the browser window.
- `data-affiliate-link`: `string` Affiliate tracking link.

### Step 2
Add the following script block to your page at the bottom of the `body`. This injects the widget into the previously created `<a>` tag.

```html
  <script>
    (function(d, s, id) {
      var js, fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s); js.id = id;
      js.src = "https://widgets.transferwise.com/widgets.js";
      fjs.parentNode.insertBefore(js, fjs);
    }(document, "script", "transferwise-wjs"));
  </script>
```

## Known limitations
* It's currently only possible to render more than a single widget per page.
