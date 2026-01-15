# Toggle Geo Map Panel in GC Fly Tours

## Version 3

Depends on the knowledge that there is a `<button>` element that contains a `title` attribute with value "Toggle Geotag Map"

```html
<button title="Toggle Geotag Map">...</button>
```

```javascript
/**
 * Dispatches a javascript click event bound to an HTML Element.
 * 
 * @param {HTMLElement} elem any clickable element
 */
var simulateClick = function (elem) {
    var evt = new MouseEvent('click', {
        bubbles: true,
        cancelable: true,
        view: window
    });
    var canceled = !elem.dispatchEvent(evt);
};

/**
 * Toggles the Geo Map panel open depending on which button with title "Toggle Geotag Map"
 *     is present in the DOM.
 * @var {HTMLElement} toggleButton button with title "Toggle Geotag Map"
 */
(function toggleGeoMap() {
    var toggleButton = document.querySelector('button[title="Toggle Geotag Map"]');
    if (toggleButton) {
        simulateClick(toggleButton);
    }
})();
```
