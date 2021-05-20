# GoLive, releasing a website

Congratulations, your website is ready to be released in the open world wide interwebz. Before you call it a project, there are some things to keep in mind.

## GoLive checklist

- [x] **Upload the website** to the internet and clear your browser and CMS caches. If you don’t want to do that publicly yet, you can do that on some hidden subdomain like `secretly-test.my-website.com`. But it is important to also test under real live circumstances.

- [x] Check if the **SSL certificate** works
The website should be accessable via `https://` and should be redirected from `http://` to `https://`.
You can do that in your `.htaccess`:
```
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```
Once you go https, make sure that all your assets are also referenced via https. Browsers won’t allow the use of different protocols within one website.

- [x] Visit your website with **different browsers on different devices**. The minimum you will have to do is
- Chrome on desktop
- Safari on iOS
But Firefox and Safari on desktop are also widely used. Also ask a friend or college to visit the website from their devices.
Many desktop browsers can simulate how your website woul look on mobile. That’s really helpful, but on a real phone it’s still always different.

- [x] Open the **browser console** and check for any errors or warnings while surfing your website.

- [x] Go to the **"network" tab** in your browser console and check if there are any resources that take really long to load.
Sometimes it happens, that images are very large or weren’t resized properly. Consider making your images smaller, use some lazyloading technique and `srcset` to provide different image sizes for each device size.

And sometimes it happens, that JS files block all other assets from loading when you add them too early in your website. Consider placing it later or at the end of the website or to use some `async`or `defer` settings.

Sometimes it happens, that webfonts are only loaded after the CSS and HTML has been parsed. You can solve that with preloading:
```
<link rel="preload" href="/assets/fonts/webfont.woff2" as="font" type="font/woff2" crossorigin>
```

Sometimes it happens, that it takes a long time for a browser to verify an external resource host. You can speed that up with
```
<link rel="preconnect" href="https://external-resource.host/some-external-asset.js">
```

- [x] Add **[server side compression](https://kinsta.com/de/blog/gzip-komprimierung-aktivieren/)** of text files, e.g. add this to your `.htaccess`:
```
<IfModule mod_deflate.c>
  <FilesMatch "\.(txt|html|md|css|js|json|xml|woff|woff2|svg)$" >
    SetOutputFilter DEFLATE
  </FilesMatch>
</IfModule>
```

- [x] Enable **browser caching**, e.g. by add this to your `.htaccess`:
```
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresDefault "access 2 years"
</IfModule>
```
> This keeps everythigng in cache for 2 years, so once you make changes to one of your assets, remember to rename it or add a query parameter for [cache busting](https://css-tricks.com/strategies-for-cache-busting-css/): `styles.css?version=2`.

- [x] Add a **`sitemap.xml`** file
- [sitemaps.org](https://www.sitemaps.org/protocol.html) official documentation
- [Docy by Google](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap?hl=de)
- [Kirby plugin](https://getkirby.com/plugins/kirbyzone/sitemapper)

- [x] Add **`robots.txt`** file
Add a `robots.txt` file to the root of your website to dis/allow crawlers to index your subpages.
```
User-agent: *
Disallow: /admin/
Sitemap: /sitemap.xml
```

- [x] Check **OpenGraph** metadata
Go to the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) and paste your website URL to get a preview of what social media platforms show, when your link is being posted.

- [x] If you use **PHP**, check the current version of the server. If it’s `<=7.3`, it might be worth updating. (as of 2021, current versions are `7.4` or `8`).

- [x] If you manage your own server, check if **[HTTP/2](https://tools.keycdn.com/http2-test)** is enabled.

- [x] Go to **[Google PageSpeed](https://developers.google.com/speed/pagespeed/insights)** and test your website performance.
