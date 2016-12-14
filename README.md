# Transclusion

## Overview

We've already used the `transclude` property, but we don't quite know what it is yet. Let's see how we can use the `transclude` property to customize content inside of our directives. 

## Objectives

- Describe transclusion
- Describe the "transclude" property
- Use transclusion to inject DOM nodes into our Directive
- Use ng-transclude

## Transclusion

Say we want to be able to customize the content inside of our directives, like so:

```html
<our-directive>
	Content here! We want to put custom content in our directive!
</our-directive>
```

Up until now, any content *inside* the directive would be replaced by our template. However, we can change that and actually put the content into our template, and also control where we want to put it - awesome!

To do this, we add a property named `transclude` to our directive. We will set this to `true` for now. This lets us use the `ng-transclude` directive.

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
	<div class="ourDirective">
		The content of our directive is: <span>Content here! We want to put custom content in our directive!</span>
	</div>
</our-directive>
```

## Resources
* (Transclusion in 120 Seconds)[https://www.youtube.com/watch?v=HnYT3Wq2iS8]
<p class='util--hide'>View <a href='https://learn.co/lessons/angular-transclusion-readme'>Angular Transclusion </a> on Learn.co and start learning to code for free.</p>
