# GoLive, releasing a website

Congratulations, your website is ready to be released in the open world wide interwebz. Before you call it a project, there are some things to keep in mind.

## GoLive checklist

### Test on live server
Upload the website to the internet and clear your browser and CMS caches. If you don’t want to do that publicly yet, you can do that on some hidden subdomain like `secretly-test.my-website.com`. But it is important to also test under real live circumstances.

### SSL
The website should be accessable via `https://` and should be redirected from `http://` to `https://`.
You can do that in your `.htaccess`:
```
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```
Once you go https, make sure that all your assets are also referenced via https. Browsers won’t allow the use of different protocols within one website.

In case you don’t have access to a SSL certificate, check if you can create a free [Let’s encrypt](https://letsencrypt.org) certificate. If not, redirect `https` to `http`.

### www or not?
Decide if you want to have `www.` as part of your domain or not, but choose one option, don’t allow both. E.g. to remove the `www.` add this to your `.htaccess`:
```
RewriteCond %{HTTP_HOST} ^www.my-website.com$ [NC]
RewriteRule ^(.*)$ https://my-website.com/$1 [R=301,L]
```

### Browsers and devices
Visit your website with different browsers on different devices. The minimum you will have to do is:
- Chrome on desktop
- Safari on iOS

But Safari and Firefox on desktop are also [widely used](https://gs.statcounter.com/browser-market-share). Also ask a friend or college to visit the website from their devices. Many desktop browsers can simulate how your website woul look on mobile. That’s really helpful, but on a real phone it’s still always different.

### Validate your code
- [HTML markup validator](https://validator.w3.org)
- [CSS code validator](https://jigsaw.w3.org/css-validator/)
- [Check for broken links](https://validator.w3.org/checklink)

### Check browser console
Open the browser console and check for any errors or warnings while surfing your website.

### Minify CSS and JS
You want to organize your code files in a way that is best readable for human beings. However, that might cost additional file weight. Consider minifying (or uglifying) your code before shipping it. There are copy and paste tools for [CSS](https://cssminifier.com) and [JS](https://javascript-minifier.com) and also plugins that you can integrate into your automated workflow (e.g. [Gulp](https://gulpjs.com) or package bundler like [webpack](https://webpack.js.org)).

### Check loading of assets
Go to the "network" tab in your browser console and check if there are any resources that take really long to load.
- Sometimes **images** are very large or weren’t resized properly. Consider making your images smaller, use some lazyloading technique and [`srcset`](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) to provide different image sizes for each device size.
- Sometimes **JS** files block all other assets from loading when you add them too early in your website. Consider placing it later or at the end of the website or to use some [`async` or `defer`](https://javascript.info/script-async-defer) settings.
- Sometimes **webfonts** are only loaded after the CSS and HTML has been parsed. You can speed that up with preloading:
```
<link rel="preload" href="/assets/fonts/webfont.woff2" as="font" type="font/woff2" crossorigin>
```
- Sometimes browsers need time to **verify external hosts**. You can speed that up with preconnect:
```
<link rel="preconnect" href="https://external-resource-host.com">
```

See [Prefetching Preloading Prebrowsing](https://css-tricks.com/prefetching-preloading-prebrowsing/) by CSS Tricks

### Compression
Add gzip compression of text files, e.g. add this to your `.htaccess`:
```
<IfModule mod_deflate.c>
  <FilesMatch "\.(txt|html|md|css|js|json|xml|woff|woff2|svg)$" >
    SetOutputFilter DEFLATE
  </FilesMatch>
</IfModule>
```

### Browser caching
So browsers can keep your asets in cache and don’t have to download them a second time. E.g. by add this to your `.htaccess`:
```
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresDefault "access 2 years"
</IfModule>
```
> This keeps everythigng in cache for 2 years, so once you make changes to one of your assets, remember to rename it or add a query parameter for [cache busting](https://css-tricks.com/strategies-for-cache-busting-css/): `styles.css?version=2`.

### PHP Version
Check the current PHP version the server uses. If it’s `7.3` or lower, it might be worth updating. As of Spring 2021, current versions are `7.4` and `8`. You should be able to upgrade `7.x` versions without breaking stuff. When upgrading from `5.x`, test all features of your website afterwards.

### HTTP/2
If you manage your own server, [check if HTTP/2](https://tools.keycdn.com/http2-test) is enabled. This enables servers to answer multiple reguest within one single response, which speeds up your waiting time.

### sitemap.xml
A sitemap provides a complete collection of all subpages and images to a bot or even a person:
- [sitemaps.org](https://www.sitemaps.org/protocol.html) official documentation
- [Google Tutorial](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap?hl=de)
- [Kirby plugin](https://getkirby.com/plugins/kirbyzone/sitemapper)

### robots.txt
Add a `robots.txt` file to the root of your website to dis/allow crawlers to index your subpages.
```
User-agent: *
Disallow: /admin/
Sitemap: /sitemap.xml
```

### OpenGraph metadata
Go to the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) and paste your website URL to get a preview of what social media platforms show, when your link is being posted.

### Let the tests begin
- [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights)
- [Sitechecker](https://sitechecker.pro)
- [web.dev Measure](https://web.dev/measure/)

## Read more

- [Fast load times](https://web.dev/fast/#lazy-load-images-and-video) on web.dev
