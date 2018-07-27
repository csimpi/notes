I've found a workaround without changing the script, I'm going to share it to help others:

1. Set the default message to false (this way we can add custom html template).
2. Set a new template that accepts custom variable (state.html).

```
    blockUIConfig.message = false;
    blockUIConfig.template = '' +
        '<div class="block-ui-overlay" ng-class="state.overlayClass"></div>' +
        '<div class="block-ui-message-container" aria-live="assertive" aria-atomic="true">' +
        '   <div class="block-ui-message" ng-class="$_blockUiMessageClass" ng-if="state.message">' +
        '       {{ state.message }}' +
        '   </div>' +
        '       <div bind-html-compile="state.html"></div> ' +
        '</div>';
```

3. Start blockUI with the parameters below

```
        blockUI.start({
                message: false,
                overlayClass: 'custom-class', //You can add custom class for the blockUI overlay
                html: '<h1>Custom message with HTML</h2><p>This is a custom message with HTML</p>' ,
        });
```

4. Add a directive that compiles the HTML to AngularJS object. This is important only if you want to use AngularJS directives in the HTML code (for example ng-click).
If you don't wanna add this directive, you can change `bind-html-compile` to `ng-bind-html`. In this case you won't be able to use AngularJS directives, and your HTML will be stripped if you don't use `$sce` before passing the HTML to the blobkUI instance.

```
.directive('bindHtmlCompile', ['$compile', function ($compile) {
    return {
        restrict: 'A',
        link: function (scope, element, attrs) {
            scope.$watch(function () {
                return scope.$eval(attrs.bindHtmlCompile);
            }, function (value) {
                element.html(value);
                $compile(element.contents())(scope);
            });
        }
    };
}]);
```
