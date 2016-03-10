# Transclusion

## Objectives

We've already used the `transclude` property, but we don't quite know what it is yet.

## Instructions

- Describe transclusion
- Describe the "transclude" property
- Use transclusion to inject DOM nodes into our Directive
- Use ng-transclude

## Transclusion

Say we want to be able to use our directive like this:

```html
<our-directive>
	Content here! We want to put custom content in our directive!
</our-directive>
```

Up until now, any content *inside* the directive would be replaced by our template. However, we can change that and actually put the content into our template, and also control where we want to put it - awesome!

To do this, we add a property named `transclude` to our directive. We will set this to `true` for now.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is:',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

We can then use the directive `ng-transclude` to put our content wherever we want it in our template.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is: <span ng-transclude></span>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

It's as simple as that! When Angular runs, we will end up with this rendered in the HTML:

```html
<our-directive>
	<div calss="ourDirective">
		The content of our directive is: <span>Content here! We want to put custom content in our directive!</span>
	</div>
</our-directive>
```
