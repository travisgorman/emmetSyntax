# Emmet Abbreviations Syntax


___
## Nesting

### Child: `>`
use `+` to place elements inside each other


### Sibling: `+`
use `+` to place elements on the same level of nesting



___

## Climbing Up: `^`
climb back out a level in the tree, so in the following example, after the `<em>` tag, I am still inside the `<p>`, 

		div+div>p>span+em

```html
		<div></div>
		<div>
			<p>
				<span></span>
				<em></em>
			</p>
		</div>
```

so if I want a `<blockquote>` as a sibling of `<p>`, I would need to climb up a level

		div+div>p>span+em^bq

```html
<div></div>
<div>
	<p>
		<span></span>
		<em></em>
	</p>
	<blockquote></blockquote>
</div>
```

___
## Grouping `()`
use `()` to group subtrees in complex abbreviations

		div>(header>ul>li*2>a)+footer>p

```html
<div>
	<header>
		<ul>
			<li><a href="#">This</a></li>
			<li><a href="#">That</a></li>
		</ul>
	</header>
	<footer>
		<p>This is a tagline</p>
	</footer>
</div>
```

___

## Multiplication `*`
use `*` to define how many elements you'd like outputted

		ul>li*5

```html
<ul>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
</ul>
```

___

## Attribute Operators
similar to CSS, `.class` and `#id`

		div#header+div.page+div#footer.class1.class2.class3


```html
<div id="header">
	Header
</div>
<div class="page">
	Page
</div>
<div id="footer" class="class1 class2 class3">
	Footer
</div>
```

with spacing to show elements

		div#header + div.page + div#footer.class1.class2.class3


### Custom Attributes
similar to CSS, use `[attr]` to add custom attributes to your element

* you can place as many attributes as you like inside square brackets
* you don't have to specify attribute values (tabstops instead)
* you can use single or double quotes
* you don't need quotes if the value doesn't contain spaces

		td[title="Hello World!" colspan=3]

```html
<td title="Hello World!" colspan="3"></td>
```

___


### Item Numbering: `$`
with the multiplication `*` operator, you can repeat elements, numbering them with `$`

		ul>li.item$*5

```html
<ul>
	<li class="item1"></li>
	<li class="item2"></li>
	<li class="item3"></li>
	<li class="item4"></li>
	<li class="item5"></li>
</ul>
```

* use multiple `$$$` to pad with zeros 

#### Change numbering base and direction with `@-` after `$`


___

## Add Text: `{}`
use curly braces to add text to any element

		a{Click me}

```html
<a href="#">Click me</a>
```

___


## Element Types 

All Emmet elements definitions are stored in `snippets.json` file in the following format:

```json
{
    "html": {
        "abbreviations": {
            "a": "<a href=\"\">",
            "link": "<link rel=\"stylesheet\" href=\"\" />"
            ...
        },
        "snippets": {
            "cc:ie6": "<!--[if lte IE 6]>\n\t${child}|\n<![endif]-->"
            ...
        }
    },

    "css": {
        ...
    }
}
```

## Snippets and Abbreviations

snippets are just the same as how they are in Sublime Text

* element name
* default attributes
* attributes order
* attributes default values
* should element contain closing tag



		link

```html
<link rel="stylesheet" href="#">
```


### abbreviations

		bq

```html
<blockquote></blockquote>
```

___

## Implicit Tag Names

when adding attributes, the default element is `div`

	.content

```html
<div class="content"></div>
```

Resolve tag based on the parent

* `li` for `ul` and `ol`
* `tr` for `table`, `tbody`, `tfoot`
* `td` for `tr`
* `option` for `select` and `optgroup`


		.wrap>.content

```html
<div class="wrap">
	<div class="content"></div>
</div>
```

		em>.info

```html
<em><span class="info"></span></em>
```

		ul>.item*3

```html
<ul>
	<li class="item"></li>
	<li class="item"></li>
	<li class="item"></li>
</ul>
````

		table>#row$*5>[colspan=2]

```html
<table>
	<tr id="row1">
		<td colspan="2"></td>
	</tr>
	<tr id="row2">
		<td colspan="2"></td>
	</tr>
	<tr id="row3">
		<td colspan="2"></td>
	</tr>
	<tr id="row4">
		<td colspan="2"></td>
	</tr>
	<tr id="row5">
		<td colspan="2"></td>
	</tr>
</table>
```

___

## Lorem Ipsum Generator


		lorem

generates a 30 word snippet of lorem text. Default is 30 words, and you can specify how many words should be generated

		lorem10

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facere, est!			

		p*4>lorem10

```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aspernatur, sunt.</p>
<p>Perferendis ea, perspiciatis dolorem dignissimos doloribus repellat saepe dolore repudiandae.</p>
<p>Quas doloremque sit ea a, et aut error in dolores!</p>
<p>Autem, assumenda, facilis. Assumenda delectus numquam, soluta! Maxime, ut, recusandae.</p>
```

lorem also uses the implicit tag name generator. 

		ul.generic-list>lorem10.item*4

```html
<ul class="generic-list">
	<li class="item">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Excepturi, numquam?</li>
	<li class="item">Id debitis inventore tempora aut, ipsum ab saepe quas iste.</li>
	<li class="item">Dolorem a error cupiditate, libero beatae nisi eum accusantium perferendis.</li>
	<li class="item">Laboriosam doloribus nisi blanditiis voluptatum aliquid sed voluptate culpa facilis.</li>
</ul>
```		














































