# iOS Web App's

There are a lot of things you have to setup to cover all Apple devices when creating a Web App. I will keep track of them here.

##App Titles and viewports
Here we setup viewports, so the app is the correct width (device width), fullscreened and the title for your web app. The viewport tag is iPhone 5 friendly as the usual viewport tags people hve found to have issues with.

    <!-- Viewport (iPhone 5 friendly) -->
    <meta name="viewport" content="initial-scale=1.0">
    <!-- Fullscreen -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <!-- Title -->
    <meta name="apple-mobile-web-app-title" content="App Title">
    
##App Icons
Sigh. Theres a lot of different sizes needed to fit certain sized devices and their retina versions. Each line also has it's precomposed version to 

    <!-- iPhone 3GS & 2011 iPod Touch (57x57) -->
    <link rel="apple-touch-icon" href="/path">
    <link rel="apple-touch-icon-precomposed" href="/path">
    
    <!-- iPhone iPad, iPad 2 & iPad mini (72x72) -->
    <link rel="apple-touch-icon" sizes="72x72" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/path">
    
    <!-- iPhone 4, 4S, 5 & 2012 iPod Touch (114x114) -->
    <link rel="apple-touch-icon" sizes="114x114" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/path">
    
    <!-- iPad 3 & 4 -->
    <link rel="apple-touch-icon" sizes="144x144" href="/path">
    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/path">




<!-- iPhone -->
<link rel="apple-touch-startup-image"
      media="(device-width: 320px)"
      href="/assets/phone-icons/startup-320x460.png">
<!-- iPhone (Retina) -->
<link rel="apple-touch-startup-image"
      media="(device-width: 320px)
         and (-webkit-device-pixel-ratio: 2)"
      href="/assets/phone-icons/startup-640x920.png">
<!-- iPad landscape -->
<link rel="apple-touch-startup-image" sizes="1024x748" href="/assets/phone-icons/startup-1024x748.png" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : landscape)">
<!-- iPad Portrait -->
<link rel="apple-touch-startup-image" sizes="768x1004" href="/assets/phone-icons/startup-768x1004.png" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : portrait)">
<!-- iPad Retina landscape -->
<link rel="apple-touch-startup-image" sizes="2048x1496" href="/assets/phone-icons/startup-2048x1496.png" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 2)">
<!-- iPad Retina Portrait -->
<link rel="apple-touch-startup-image" sizes="1536x2008" href="/assets/phone-icons/startup-1536x2008.png" media="screen and (min-device-width : 481px) and (max-device-width : 1024px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio: 2)">
<script src="http://js.a.striving.me/libraries/modernizr.js"></script>