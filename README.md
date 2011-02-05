# HTML Purifier for Fuel

[HTML Purifier](http://htmlpurifier.org/) is a standards-compliant HTML filter library. HTML Purifier will not only remove all malicious code (better known as XSS) with a thoroughly audited, secure yet permissive whitelist, but it can make sure your documents are standards compliant too.

This is simple wrapper package for [Fuel](http://fuelphp.com) to help HTML Purifier usage.

# Example

Add package to config.packages array or introduce when needed by Fuel::add_package('htmlpurifier')

	public function action_index()
	{
		Fuel::add_package('htmlpurifier');

		$purifier = new HTMLPurifier();
		
		$config = HTMLPurifier_Config::createDefault();
		$config->set('HTML.Allowed','b,a[href]');
		
        $data = $purifier->purify('Purifying <i>italic</i>, <b>bold</b> <a href="fuelphp.com">Fuel</a> input',$config);
        echo $data;
	---
	This example will remove all HTML tags except allowed 'b,a[href]'.
	So output would be:
	'Purifying italic, <b>bold</b> <a href="fuelphp.com">Fuel</a> input'

Check out more instructions how to use and configure from 
[HTML Purifier documents](http://htmlpurifier.org/docs)

# Install

When using Oil Fuel command line utility. Make sure that your fuel/app/cache 
folder is writable by php.

	---
	php oil package install htmlpurifier
	---

