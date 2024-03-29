# Liquid Programming

A Templating Language

> ===== Note: All underscre ( \_ ) sectence will replace by yours without only type =====

<hr><hr>

## **_Liquid Basic for Template Developement_**

<hr><hr>

[Liquid Documentation](https://shopify.dev/docs/api/liquid/)

### **Logical Start End**

```bash
{% %}
```

### **Output print**

```bash
{{ }}
```

### **Variable Declear**

```bash
{% assign variable_name = variable_value %}
```

> Examples:
> <br> {% assign myName = "Shama" %}

### **Mathmatical Operators**

```bash
Asisgn Operator- =
Add Operator- | plus:
Substraction Operator- | minus:
Multiplication Operator- | times:
Division Operator- | divided_by:
Modulas Operator- | modulo:
```

> Examples:
> <br> Assignment Operator
> <br> ---------------------
> <br> {%  assign num1 = 10 %} <br> {%  assign num2 = 4 %} <br><br> Addition: {{ num1 | plus: num2 }}<br> Substraction: {{ num1 | minus: num2 }}<br> Multipication: {{ num1 | times: num2 }}<br> Division: {{ num1 | divided_by: num2 }}<br> Modulas: {{ num1 | modulo: num2 }}<br>

### **Conditional Operators**

```bash
Equal Operator- ==
Graterthen operator- >
Graterthen or equal operator- >=
Lessthen Operator- <
Lessthen or equal Operator- <=
And operator- and
Or operator- or
Checks for strings operator- contains
```

> Examples:
> <br> {% if num1 > num2 and num1 > num3 %} <br> Grater number is {{ num1 }} <br> {% else %} <br> {{ num1 }} is not grater number <br> {% endif %} <br>

### **Types in shopify**

```bash
string - Any series of characters, wrapped in single or double quotes.
number - Numeric values, including floats and integers.
boolean - A binary value, either true or false.
nil - An undefined value.
Anchor to section titled '[object Object]'
array - A list of variables of any type.
empty - An empty object is returned if you try to access an object that is defined, but has no value.
```

### **[Whitespace control](https://shopify.dev/docs/api/liquid/basics#whitespace-control)**

> - hypen remove the white space

```bash
{%- if collection.products.size > 0 -%}
```

## **[Conditional Tag](https://shopify.dev/docs/api/liquid/tags/conditional-tags)**

### **[if elsif and else condition](https://shopify.dev/docs/api/liquid/tags/if)**

```bash
{% if your_condition %}
        Your_Output
    {% elsif your_condition %}
        Your_Output
    {% else %}
        Your_Output
{% endif %}
```

> Examples:
> <br> {% if num1 > num2 %} <br> Grater number is {{ num1 }} <br>{% elsif num1 < num2  %} <br>Grater number is {{ num2 }} <br> {% else num1 == num2 %} <br> Both are equal <br> {% endif %} <br>

### **[unless condition](https://shopify.dev/docs/api/liquid/tags/unless)**

> unless user for if oposite

```bash
{% unless condition %}
  expression
{% endunless %}
```

### **[Switch Case](https://shopify.dev/docs/api/liquid/tags/case)**

```bash
{% case your_input %}
    {% when your_condition %}
        Your_Output
    {% when your_condition %}
        Your_Output
    {% when your_condition %}
        Your_Output
    {% else %}
        Your_Output
{% endcase %}
```

> Examples:
> <br>{% assign color= "black" %}<br><br> {% case color %} <br> {% when "red" %} <br> Color is {{ color }} <br> {% when "green" %} <br> Color is {{ color }} <br> {% when "blue" %} <br> Color is {{ color }} <br> {% else %} <br> Your color is not listed <br> {% endcase %}

## **[Iteration tags](https://shopify.dev/docs/api/liquid/tags/iteration-tags)**

### **[for loop](https://shopify.dev/docs/api/liquid/tags/for)**

```bash
{% for variable in array %}
  expression
{% endfor %}
```

<hr><hr>

## **[Syntex tags](https://shopify.dev/docs/api/liquid/tags/syntax-tags)**

### **[Comment](https://shopify.dev/docs/api/liquid/tags/comment)**

> Multiline comment

```bash
{% comment %}
  content
{% endcomment %}
```

> Single line comment

```bash
{% # content %}
```

## **[Syntex tags](https://shopify.dev/docs/api/liquid/tags/syntax-tags)**

## **_Template Development_**

<hr><hr>

[Template Documentation](https://shopify.dev/themes/getting-started/create)

### **Stylesheet add**

```bash
<link rel="preload" href="{{ 'your_css_file_name.css' | asset_url }}" as="style">
```

### **Script add**

```bash
<link rel="preload" href="{{ 'your_js_file_name.js' | asset_url }}" as="script">
```

### **Section Call**

Section call in the template page

```bash
{% section 'your_section_file_name' %}
```

> Examples:
> <br> {% section 'demo' %}

### **Schema Design**

Schema design like as a JSON format

```bash
{% schema %}
  {
    "name": "section_name",
    "settings": [
      {
        "type":"which_type_you_want",
        "id":"an_uique_id",
        "label":"which_show_in_the_theme_customization",
        "default":"section_default_value"
      },
      {
        "type":"which_type_you_want",
        "id":"an_uique_id",
        "label":"which_show_in_the_theme_customization",
        "default":"section_default_value"
      }
    ]
  }
{% endschema %}
```

> Examples:
> <br> {% schema %} <br> { <br> "name": "Custom", <br> "settings": [ <br> { <br> "type":"text", <br> "id":"textid", <br> "label":"Enter Your Text", <br> "default":"This is custom section" <br> } <br> ] <br> } <br> {% endschema %} <br>

### **Schema Call**

Schema call in the section page

```bash
{{ section.settings.your_section_id }}
```

> Examples:
> <br> {{ section.settings.textid }}

### **Presets Design**

Presets use for make the section available for all pages. Presets use in schema after settings

```bash
{% schema %}
  {
    "name": "section_name",
    "settings": [
      {
        "type":"which_type_you_want",
        "id":"an_uique_id",
        "label":"which_show_in_the_theme_customization",
        "default":"section_default_value"
      }
    ],
    "presets":[
      {
        "name":"section_name_which_is_show_in_add_section",
        "category":"section_type/category"
      }
    ]
  }
{% endschema %}
```

> Examples:
> <br> "presets":[ <br> { <br> "name":"Custom Text", <br> "category":"text" <br> } <br> ] <br>

### **Image Picker**

Image picker get the custom image from user. Image picker use in schema setting

```bash
    {
    "type":"image_picker",
    "id":"an_unique_id",
    "label":"Select Your image"
    }
```

> Examples:
> <br> { <br> "type":"image_picker", <br> "id":"myimage", <br> "label":"Select Your image" <br> } <br>

### **Image Call**

Image picker get the custom image from user. Image picker use in schema setting

```bash
<img src="{{ section.settings.image_picker_id | img_url: "size_in_pixels" }}" />
```

> Examples:
> <br> <img src="{{ section.settings.myimage | img_url: "1920x" }}" />

### **Slider Schema**

Slider Schema use for slide image

```bash
{% schema %}
  {
    "name": "schema_name",
    "blocks": [
     {
       "name": "block_name",
       "type": "slide",
       "settings": [
         {
           "type": "image_picker",
           "id": "image_picker_id",
           "label": "image_picker_label"
         }
       ]
     }
  ]
  }
{% endschema %}
```

> Examples:
> <br> {% schema %} <br> { <br> "name": "Slider", <br> "blocks": [ <br> { <br> "name": "Slide", <br> "type": "slide", <br> "settings": [ <br> { <br> "type": "image_picker", <br> "id": "image", <br> "label": "Image" <br> } <br> ] <br> } <br> ] <br> } <br> {% endschema %}

### **Snippets**

Snippets is the small part of section. It is used for store html code and it called in section page

```bash
{% include 'Snippets_name' %}
```

> Examples:
> <br> {% include 'demo' %}

### **Theme Setting call**

```bash
{{ settings.schema_settings_id }}
```

> Examples:
> <br> {{ settings.text }}
