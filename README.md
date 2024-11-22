# copy-to-clipboard

This is a clone of James Warren's aka "Sancarn" useful copy-to-clipboard project ['https://github.com/sancarn/copy-to-clipboard'](https://github.com/sancarn/copy-to-clipboard).

## Usage

Links like [`https://ghutches.github.io/copy-to-clipboard/index.html?copy=orange`](https://ghutches.github.io/copy-to-clipboard/index.html?copy=orange) will copy `orange` to the clipboard (as long as the user enables it).

> Note: This uses the `Clipboard` API and isn't anything to shout home about. This will not be compatible with old browsers.

## Usage in sharepoint lists

The initial reason I created this site is a workaround to inflexible sharepoint APIs / security. In sharepoint you can add format JSON to fields, to format data in a different way. I wanted to add a button to a field which would allow the user to copy the data within. Unfortunately this cannot be done with the sharepoint site alone, so the work around is to use a seperate helper site.

This will add a copy icon and a link such that when you click on the field, the data will be copied to the clipboard:
```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "a",
  "attributes": {
    "iconName": "Copy",
    "target": "_blank",
    "class": "ms-borderColor-white ms-borderColor-themePrimary--hover",
    "href": "='https://ghutches.github.io/copy-to-clipboard/index.html?copy=' + @currentField"
  },
  "style": {
    "color": "#272727",
    "text-decoration": "none",
    "font-size": "14px",
    "border-bottom-width": "1px",
    "border-bottom-style": "solid",
    "min-width": "400px"
  },
  "children": [
    {
      "elmType": "span",
      "txtContent": "@currentField",
      "style": {
        "padding-left": "5px"
      }
    }
  ]
}
```
