# MaxLength
JQuery plugin to restrict the input number field to its max length.

    (function ($) {
        $.fn.maxLength = function (options) {
            // This is the easiest way to have default options.
            var settings = $.extend({
                // These are the defaults.
                maxLength: 10
            }, options);

            return this.each(function () {
                $(this).keypress(function (event) {
                    event = event ? event : window.event;
                    var keyCode = event.which ? event.which : event.keyCode;
                    if (!(keyCode > 31 && (keyCode < 48 || keyCode > 57))) {
                        var maxlength = $(this).attr("maxlength") ? parseInt($(this).attr("maxlength")) : settings.maxLength;
                        return $(this).val().length >= maxlength ? false : true;
                    } else {
                        return false;
                    }
                });
            });
        };
    }(jQuery));

   # Calling maxLength jQuery Plugin
        $(function () {
            $(".number").maxLength();
        });
    
    # Input field
    <input type="number" class="number" maxlength="5" />
