# Emmet Abbreviations Syntax


## Nesting

### Child: `>`
use `+` to place elements inside each other


### Sibling: `+`
use `+` to place elements on the same level of nesting


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




