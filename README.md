# Inline Read More-Read Less Plugin jQuery

[![forthebadge](https://forthebadge.com/images/badges/fuck-it-ship-it.svg)](#)  [![forthebadge](https://forthebadge.com/images/badges/does-not-contain-treenuts.svg)](#)

![dev-asshole](https://img.shields.io/badge/developer-asshole-%230b50a7.svg) ![Shippable](https://img.shields.io/shippable/5444c5ecb904a4b21567b0ff.svg) ![Shippable](https://img.shields.io/badge/Developer-Single-%23a6a903.svg) 


Adds Inline Read More and  Read Less button in jquery.


## Usage

Shortens the text within 'element' and add a 'more' link.

    $(element).shorten();

Add a link with text 'Read More' while shortening the content of element.

	$(element).shorten({
	moreText: 'Read More'
	});

Change the link text to 'Show More' and 'Show Less' overriding default value 'Read More' and 'Read Less'.

	$(element).shorten({
	moreText: 'Show More',
	lessText: 'Show Less'
	});

Override default display 400 characters and hide text above 150 characters.

	$(element).shorten({
	showChars: 150,
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



[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)
