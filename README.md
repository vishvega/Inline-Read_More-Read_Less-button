# Inline-Read_More-Read_Less-button
Adds Inline Read More and  Read Less button in jquery.


## Usage

Shortens the text within 'element' and add a 'more' link.

    $(element).shorten();

Add a link with text 'read more' while shortening the content of element.

	$(element).shorten({
	moreText: 'read more'
	});

Change the link text to 'read more' and 'read less' overriding default value 'more' and 'less'.

	$(element).shorten({
	moreText: 'read more',
	lessText: 'read less'
	});

Override default display 100 characters and hide text above 50 characters.

	$(element).shorten({
	showChars: 50,
	});


Parameters
----------

-------------------------------------------------------------------------------------------------------------------------------
`showChar`			|Total characters to show to user. If the content is more then showChar, it will be split into two halves and first one will be showed to user. 

`ellipsesText`	| The text displayed before “ReadMore” link. Default is “…”  

`moreText`			| The text shown in more link. Default is “ReadMore”. You can change to ">>" or "show more" 

`lessText` 			| The text shown in less link. Default is “ReadLess”. You can change to "<<" or "show less"

`onMore` 				| Callback function to trigger when "ReadMore" is clicked 

`onLess` 				| Callback function to trigger when "ReadLess" is clicked


- Liceced under GNU General Public License v3.0.
