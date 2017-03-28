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





























