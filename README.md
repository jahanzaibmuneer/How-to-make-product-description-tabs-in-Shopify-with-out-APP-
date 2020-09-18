# How to make product description tabs in Shopify with out APP?

Step 1: First you need to open you theme code. In templates folder find the file product.liquid

Step 2: In the product.liquid you will see {% section 'product-template' %}. Open this file from sections folder.

Step 3: Find the following code in product-template.liquid

{{ product.description }}

and replace it with the following code in file product-template.liquid (see file in the repository):

Step 4: In schema code append the following code in the settings array
{
  "type": "checkbox",
  "id": "enable_description_tabs",
  "label": "Enable Description Tabs",
  "default": true,
  "info": "Heading 6 titles will be converted to tab headings, tab content will be everything between the Heading 6 titles."
}

Step 5: Create a snippet named it 'product-tabs' and put the code from product-tabs.liquid (see file in the repository).
