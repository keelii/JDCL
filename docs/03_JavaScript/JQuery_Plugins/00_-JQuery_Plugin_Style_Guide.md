## jQuery 插件开发规范

### 一、插件设计模式
插件开发遵循「<abbr title="Simple, Easy, Scalable">SES</abbr> 原则」， 即：简单、易用、可扩展
```javascript
(function ($) {
    /**
     * pluginName插件
     */
    var pluginName = function (that, options, callback) {

        this.opts = $.extend({
            options: 'options you want to set'

        }, options);

        this.$o = $(that);
        this.callback = callback || function() {};

        this.init();
    };

    pluginName.prototype = {
        init: function() {
            // 插件入口
        },
        onComplate: function() {
            if ( typeof this.callback === 'function' ) {
                this.callback.apply(this.$o, ['[args] you want to return to callback']);
            }
        }
    };

    $.fn.pluginName = function (options, callback) {

        return this.each(function () {
            // 实例化插件对象
            var plugin = new pluginName(this, options, callback);

            $(this).data('pluginName', plugin);
        });
    };
}(jQuery));
```