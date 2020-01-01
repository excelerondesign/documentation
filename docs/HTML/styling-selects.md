---
id: styling-selects
title: Styling select elements: tips
sidebar_label: Styling Select Elements
---

Styling `<select>` elements is tricky. One thorn is dealing with rounded corners inside of default browser stylesheets.

To remove this add these styles:
```css
select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
```
This sets the `appearance` back to initial, and gives complete style control back to us.

See below example:
<style>
  select {
    display: block;
    width: auto;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    color: #495057;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    margin-bottom: .25rem;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
    padding: .25rem;
  }
  select.styled {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
  }
  .container-light {
    background-color: #f7f7f7;
    padding: 2rem 1.5rem;
    display: flex;
    align-items:center;
    justify-content: space-around;
  }
</style>
<div class="container-light">
  <select>
    <option>Item 1</option>
  </select>
  <select class="styled">
    <option>Item 1</option>
  </select>
</div>  

*the select on the left is base styles + bootstrap, the select on the right removes the appearance attribute*
