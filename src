/*
Original code by Viralpatel (https://github.com/viralpatel/jquery.shorten), and 
Cauldrath (https://github.com/Cauldrath/jquery.shorten).
Updated code to that show both ReadMore and ReadLess buttons right after paragraph/text ended.(both being inline).

ReadMore ReadLess jQuery plugin.
Vishwa.
Version 1.0.0
Liceced under GNU General Public License v3.0.


*/



(function($) {
    $.fn.shorten = function(settings) {
        "use strict";

        var config = {
            showChars: 400,     //Number of characters to show
            minHideChars: 10,   //minimum numbers of characters to hide
            ellipsesText: "...",    //text that indicates there's more (abcdef...)
            moreText: "Read More",  //button text for read more/expand
            lessText: "Read Less",  //button text for collapse
            inlineMore: true,       //enable or disable put read more/less buttons inline
            onLess: function() {},
            onMore: function() {},
            errMsg: null,
            force: false
        };

        if (settings) {
            $.extend(config, settings);
        }

        function moreLink(text, classText) {
          return '<span><a href="javascript://nop/" class="morelink ' + (classText || '') + '">' + text + '</a></span>';
        }
		
		

        if ($(this).data('jquery.shorten') && !config.force) {
            return false;
        }
        $(this).data('jquery.shorten', true);

        $(document).off("click", '.morelink');

        $(document).on({
            click: function() {
                var $this = $(this);
                var $short;
                var $all;
                if ($this.hasClass('less')) {
                    if(config.inlineMore) {
                      $all   = $this.closest('.allcontent');
                    } else {
                      $all   = $this.parent().prev();
                      $this.removeClass('less');
                      $this.html(config.moreText);
                    }
                    $short = $all.prev();
                    $all.animate({'height':'0'+'%'}, function () { $short.show(); }).hide('fast', function() {
                        config.onLess();
                    });

                } else {
                    if(config.inlineMore) {
                      $short = $this.closest('.shortcontent');
                      $all   = $short.next();
                    } else {
                      $all   = $this.parent().prev();
                      $short = $all.prev();
                      $this.addClass('less');
                      $this.html(config.lessText);
		      
                    }
                    $all.animate({'height':'100'+'%'}, function () { $short.hide(); }).show('fast', function() {
                        config.onMore();
                    });
                }
                return false;
            }
        }, '.morelink');

        return this.each(function() {
            var $this = $(this);

            var content = ($this.html() || '').trim();
            var contentlen = $this.text().trim().length;
            if (contentlen > config.showChars + config.minHideChars) {
                var c = content.substr(0, config.showChars);
                if (c.indexOf('<') >= 0) // If there's HTML don't want to cut it
                {
                    var inTag = false; // I'm in a tag?
                    var bag = ''; // Put the characters to be shown here
                    var countChars = 0; // Current bag size
                    var openTags = []; // Stack for opened tags, so I can close them later
                    var tagName = null;

                    for (var i = 0, r = 0; r <= config.showChars; i++) {
                        if (content[i] == '<' && !inTag) {
                            inTag = true;

                            // This could be "tag" or "/tag"
                            tagName = content.substring(i + 1, content.indexOf('>', i));

                            // If its a closing tag
                            if (tagName[0] == '/') {


                                if (tagName != '/' + openTags[0]) {
                                    config.errMsg = 'ERROR en HTML: the top of the stack should be the tag that closes';
                                } else {
                                    openTags.shift(); // Pops the last tag from the open tag stack (the tag is closed in the retult HTML!)
                                }

                            } else {
                                // There are some nasty tags that don't have a close tag like <br/>
                                if (tagName.toLowerCase() != 'br') {
                                    openTags.unshift(tagName); // Add to start the name of the tag that opens
                                }
                            }
                        }
                        if (inTag && content[i] == '>') {
                            inTag = false;
                        }

                        if (inTag) { bag += content.charAt(i); } // Add tag name chars to the result
                        else {
                            r++;
                            if (countChars <= config.showChars) {
                                bag += content.charAt(i); // Fix to ie 7 not allowing you to reference string characters using the []
                                countChars++;
                            } else // Now I have the characters needed
                            {
                                if (openTags.length > 0) // I have unclosed tags
                                {
                                    for (j = 0; j < openTags.length; j++) {
                                        bag += '</' + openTags[j] + '>'; // Close all tags that were opened

                                        // You could shift the tag from the stack to check if you end with an empty stack, that means you have closed all open tags
                                    }
                                    break;
                                }
                            }
                        }
                    }
                    c = $('<div/>').html(bag + '<span class="ellip">' + config.ellipsesText + '</span>' + (config.inlineMore ? ' ' + moreLink(config.moreText) : '')).html();
                }else{
                    c+=config.ellipsesText;
                }

                var html = '<div class="shortcontent">' + c +
                    '</div><div class="allcontent">' + content  +
                    '</div>';

                $this.html(html);
		$('.allcontent p:last').append('<a href="javascript://nop/" class="morelink less"> Read Less</a>');
		//append read less/more button at the end of the last paragraph
        
                $this.find(".allcontent").hide(); // Hide all text
                $('.shortcontent p:last', $this).css('margin-bottom', 0); //Remove bottom margin on last paragraph as it's likely shortened
            }
        });

    };

})(jQuery);
