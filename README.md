# How to make product description tabs in Shopify with out APP?

Step 1: First you need to open you theme code. In templates folder find the file product.liquid

Step 2: In the product.liquid you will see {% section 'product-template' %}. Open this file from sections folder.

Step 3: Find the following code in product-template.liquid

{{ product.description }}

and replace it with the following code:

{%- assign product_description_content = product.description -%}

{%-if section.settings.enable_description_tabs -%}
  {%- assign product_description_content = product_description_content | split: '<h6>' | first -%}
{%- endif -%}

{% if product_description_content != '' %}
  <div id="product-description">
    {{ product.description }}
  </div>
{% endif %}

{%-if section.settings.enable_description_tabs and product_description_content == '' -%}
  <div id="product-description">
    {% include 'product-tabs' %}
  </div>
{% endif  %}

Step 4: In schema code append the following code in the settings array
{
  "type": "checkbox",
  "id": "enable_description_tabs",
  "label": "Enable Description Tabs",
  "default": true,
  "info": "Heading 6 titles will be converted to tab headings, tab content will be everything between the Heading 6 titles."
}

Step 5: Create a snippet called 'product-tabs' and put the code of product-tabs (see file in the repository).
