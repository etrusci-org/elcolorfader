# ElColorfader

Let the text, background or border color of a [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement) fade through random colors.  
For a working demo/starter template open **[dist/demo.html](./dist/demo.html)** in your webbrowser. Works from the filesystem and does not have to be put on a webserver.


## Usage

### 1. Create an element

```html
<div class="cf">
    Hello cruel world
</div>
```


### 2. Include the script and start it

Just before the closing `</body>` tag, include the script and start it when the page is fully loaded.

```html
<script src="./elcolorfader.js"></script>

<script>
    window.addEventListener('load', () => {
        new ElColorfader().start()

        // If you want to use another selector than `.cf`, provide it as first argument to ElColorfader, e.g.:
        // new ElColorfader('.my-custom-selector').start()
    })
</script>
```


### 3. Element Settings

You can override the default settings by adding `data-*` attributes to an element.

- *number* `data-r-min`: Minimum red value.
- *number* `data-r-max`: Maximum red value.
- *number* `data-g-min`: Minimum green value.
- *number* `data-g-max`: Maximum green value.
- *number* `data-b-min`: Minimum blue value.
- *number* `data-b-max`: Maximum blue value.
- *number* `data-dur`: Fade duration in seconds.
- *string* `data-func`: Timing function, valid: `linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`, `step-start`, `step-end`
- *string* `data-target`: Which part of the element to colorize, valid: `text`, `background`, `border`

Here's an element with all settings included:

```html
<div 
    class="cf"
    data-r-min="70"
    data-r-max="180"
    data-g-min="70"
    data-g-max="180"
    data-b-min="70"
    data-b-max="180"
    data-dur="4.2"
    data-func="linear"
    data-target="text"
>
    Text
</div>
```


If you choose `border` as `target`, you have to set initial values for the `border-width` and `border-style` on the element. The script will only change `border-color`. E.g.:

```html
...
<!-- Either define a CSS class with initial border values and apply it to the element... -->
<style>
    .border {
        border-width: 3px;
        border-style: solid;
    }
</style>

<div class="cf border" data-target="border">
    Border
</div>

<!-- ...or apply the initial border values to the element directly -->

<div class="cf" data-target="border" style="border-width: 3px; border-style: solid;">
    Border
</div>

```
