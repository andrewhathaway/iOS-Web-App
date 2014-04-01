#iOS Web Apps

There are a lot of things you have to setup to cover all Apple devices when creating an iOS friendly Web App. I will keep track of them here.

##App Titles and viewports
Here we need to setup a few things for your application. The App Viewport (The one below is iPhone 5 friendly - People have had issues with other viewport tags), Status bar styles, Telephone number format detection, fullscreen your app (removes Safari UI elements), the App title, if this is not set it fallbacks to your title tag and finally, preventing bouncing on scroll.

A little more on the iPhone 5 viewport tag: Using width-device-width strangely makes the app height the size of a 4S and lower, it also prevents splash screens from viewing at their correct, iPhone 5, height. Below is the iPhone 5 freiendly viewport tag. 

    <!-- Viewport (iPhone 5 friendly) -->
    <meta name="viewport" content="initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    
    <!-- Status bar styles -->
    <meta name="apple-mobile-web-app-status-bar-style" content="default"/>
    <meta name="apple-mobile-web-app-status-bar-style" content="black" />
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>

    <!-- Telephone format detection -->
    <meta name="format-detection" content="telephone=no">
    
    <!-- Fullscreen -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    
    <!-- Title -->
    <meta name="apple-mobile-web-app-title" content="App Title">

    <!-- Bounces -->
    <script type="text/javascript">
      document.ontouchmove = function(e) {e.preventDefault()};
    </script>

##App Icons
Sigh. There's a lot of different sizes needed to fit certain sized devices and their retina versions. Each line also has it's precomposed version to stop iOS adding effects to the icon. The sizes for these icons are in brackets in the comments.

    <!-- iPhone 3GS & 2011 iPod Touch (57x57) -->
    <link rel="apple-touch-icon" href="/path">
    <link rel="apple-touch-icon-precomposed" href="/path">
    
    
    <!-- iPhone iPad, iPad 2 & iPad mini (72x72) -->
    <link rel="apple-touch-icon" sizes="72x72" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/path">
    
    
    <!-- iPhone 4, 4S, 5 & 2012 iPod Touch (114x114) -->
    <link rel="apple-touch-icon" sizes="114x114" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/path">
    
    
    <!-- iPad 3 & 4 (144x144) -->
    <link rel="apple-touch-icon" sizes="144x144" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/path">


##App Splash/Start screens
A few splash screen sizes are required, and also their portrait and landscape versions. 

As said above, iPhone 5 splash screens will be ignored and 4 & 4S screens will be used if your viewport tag uses 'width-device-width'. 

    <!-- iPhone (320x460) -->
    <link rel="apple-touch-startup-image" media="(device-width: 320px)" href="/path">
    
    <!-- iPhone 4 & 4S Retina (640x920) -->
    <link rel="apple-touch-startup-image" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" href="/path">
    
    <!-- iPhone 5 Retina (640x1096) -->
    <link rel="apple-touch-startup-image" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" href="/path">
    
    <!-- iPad Landscape (1024x748) -->
    <link rel="apple-touch-startup-image" sizes="1024x748" href="/path" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : landscape)">
    
    <!-- iPad Portrait (768x1004) -->
    <link rel="apple-touch-startup-image" sizes="768x1004" href="/path" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : portrait)">
    
    <!-- iPad Retina Landscape (2048x1496) --> 
    <link rel="apple-touch-startup-image" sizes="2048x1496" href="/path" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 2)">
    
    <!-- iPad Retina Portrait (1536x2008) -->
    <link rel="apple-touch-startup-image" sizes="1536x2008" href="/path" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio: 2)">
    
##Preventing links from opening in Safari
It's rather annoying that links, by default, open in Safari. This means that your apps pages suddenly jump into Safari. I found this [Gist](https://gist.github.com/irae/1042167), by [Iraê Carvalho](https://github.com/irae) that fixes this problem. Add this script into your `<head>`:

    <script type="text/javascript">
    	(function(document,navigator,standalone) {
			// prevents links from apps from oppening in mobile safari
			// this javascript must be the first script in your <head>
			if ((standalone in navigator) && navigator[standalone]) {
				var curnode, location=document.location, stop=/^(a|html)$/i;
				document.addEventListener('click', function(e) {
					curnode=e.target;
					while (!(stop).test(curnode.nodeName)) {
						curnode=curnode.parentNode;
					}
					// Condidions to do this only on links to your own app
					// if you want all links, use if('href' in curnode) instead.
					if(
						'href' in curnode && // is a link
						(chref=curnode.href).replace(location.href,'').indexOf('#') && // is not an anchor
						(	!(/^[a-z\+\.\-]+:/i).test(chref) ||                       // either does not have a proper scheme (relative links)
							chref.indexOf(location.protocol+'//'+location.host)===0 ) // or is in the same protocol and domain
					) {
						e.preventDefault();
						location.href = curnode.href;
					}
				},false);
			}
		})(document,window.navigator,'standalone');
	</script>

##Footnote
If you're reading this, I hope I have helped and if you have any questions you can find me on [Twitter](http://twitter.com/andrewhathaway). Thanks.
