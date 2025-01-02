---
layout: post
title: Custom Dropdowns without Javascript
date: 2024-11-20 13:00:00 +0100
category: Computer Science
tags: [HTML, CSS]
description: "Create a custom dropdown component with custom styling, entirely without JavaScript."
---

At work I'm creating lots of forms and all kinds of different inputs methods.
Especially dropdowns are always a pain point when styling, as the default `<select>` dropdown is not stylable.
In this post I'd like to introduce a way to create a customizable, completely stylable dropdown, only with CSS and HTML.

<div>
<fieldset class="select">
    <legend>Custom Select</legend>
    <div class="dropdown">
        <label for="option-1"><input type="radio" name="select" value="option-1" id="option-1" checked/>Option 1</label>
        <label for="option-2"><input type="radio" name="select" value="option-2" id="option-2"/>Option 2</label>
        <label for="option-3"><input type="radio" name="select" value="option-3" id="option-3"/>Option 3</label>
    </div>
</fieldset>
<style>
    .select {
        border: none;
        padding: 0;
        margin: 0;
    }

    .select input {
        appearance: none;
        outline: none;
        margin: 0;
    }

    .dropdown {
        border: 1px solid #ddd;
    }

    @media (prefers-color-scheme: dark) {
        .dropdown {
            border: 1px solid #222;
        }
    }


    label {
        display: none;
        padding: 4px;
    }

    label:has(input:checked),
    .dropdown:focus-within > label,
    .dropdown:has(input:hover:not(:checked)) > label {
        display: block;
    }

    label:has(input:checked) {
        background: #eee;
    }

    label:focus-within {
        outline: 1px solid #07f;
    }
</style>
</div>

Let's build the dropdown above step by step.

Instead of using the HTML select, we start with a radio input. Dropdowns and radio inputs fullfill the same purpose. With both input types, you can select a single value out of a list of available options.

In this example, we create a radio input with three values `option-1`, `option-2` and `option-3`. The inputs are contained in their own label which will be useful later for styling the component. All the inputs are wrapped in a `div`, which will make up the dropdown part of our component. Finally, we wrap it in a fieldset with a legend to simulate the label of a select field.

```html
<fieldset class="select">
    <legend>Custom Select</legend>
    <div class="dropdown">
        <label for="option-1"><input type="radio" name="select" value="option-1" id="option-1" checked/>Option 1</label>
        <label for="option-2"><input type="radio" name="select" value="option-2" id="option-2"/>Option 2</label>
        <label for="option-3"><input type="radio" name="select" value="option-3" id="option-3"/>Option 3</label>
    </div>
</fieldset>
```

We continue with styling the component. First, we style the fieldset and remove the default style.

```css
.select {
    border: none;
    padding: 0;
    margin: 0;
}
```

We hide the radio inputs in a way that they are still visible to screen readers. This allows users with screen readers to ineract with the field as if it were a radio input.

```css
.select input {
    appearance: none;
    outline: none;
    margin: 0;
}
```

We style the dropdown `div` and the labels to make them look like options in a select field. By default, we hide the labels.

```css
.dropdown {
    border: 1px solid #ddd;
}

label {
    display: none;
    padding: 4px;
}
```

Now to the tricky part. Remember, the labels act as an option in the select field. We show the label only if either

1. The corresponding input is checked. This corresponds to the closed dropdown state where we show only the selected value.
2. If one of the inputs is focused. This corresponds to a focused select field where all options are shown.
3. If one of the inputs which is not checked is hovered. This is necessary to avoid closing the dropdown while selecting another value with the cursor.

This thranslates into the CSS below.

```css
label:has(input:checked),
.dropdown:focus-within > label,
.dropdown:has(input:hover:not(:checked)) > label {
    display: block;
}
```

Finally, we highlight the the selected value with a different background color, as well as the outline of the focused value.

```css
label:has(input:checked) {
    background: #eee;
}

label:focus-within {
    outline: 1px solid #07f;
}
```

There are still a few things missing from this dropdown implementation.

1. Selecting multiple values is not supported, however, this might be possible by using checkboxes instead of radio inputs.
2. Adding a scrollable overflow might be necessary to support more values. This should be easy to add with a bit of CSS.
3. The options are not seachable. To implement a search functionality, JavaScript will most likely be necessary.

Many of these limitations might not be needed at all or can be easily added.

That was already it! A fully accessible, customizable and easily navigatable dropdown implemented only with a few lines of HTML and CSS.

