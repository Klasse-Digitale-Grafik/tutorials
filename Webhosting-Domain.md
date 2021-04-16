# Webhosting & Domain

A **website** and a **domain** are two different things: The **website is a collection** of files that can be rendered by your browser. These files are stored on some **server**, a computer that is always connected to the internet and which can be accessed by "calling" it’s **IP address**. And then there is a domain, which redirects your request to that servers IP address. Because on one server with one IP address, there can be multiple websites, the domain is also used by the server to determine which directory of files should be delivered.

## 🌱 The easy way
The easiest is to have domain, email and webhosting with one provider. Many providers call this product "webhosting", and often there is almost nothing that can go wrong:
- Buy a webhosting package and select an available domain
- Create an FTP user and upload your website to the webspace
- Go to domain settings and direct the domain to that directory where you uploaded the website
- (Set up an email address)

This kind of webhosting is mostly running Apache or nginx on a shared Linux machine and is suitable for simple websites made with HTML or generated with PHP, like Kirby or Wordpress.

### Specs
These are the specs that you should look for:
- Monthly cost
- Inclusive domains or SSL certificates?
- SSD disk storage with sufficient space
- CPU/RAM
- SFTP
- PHP >= 7.4
- Serverlocation (Germany/Europe)

Depending on your needs:
- Database
- Node.js
- SSH

### Providers
Some providers that offer as-easy-as-possible webhosting:
- [Netcup](https://www.netcup.de/hosting/)
`€2` 1 domain, ∞SSL, 50GB SSD
- [Hetzner](https://www.hetzner.com/de/webhosting)
`€2` 1 domain, ∞SSL, 10GB SSD
- [Velogrid](https://www.velogrid.com/)
`€3` 1 domain + 1GB / 0 domains + 10GB, ∞SSL
- [HostEurope](https://www.hosteurope.de/webhosting-loesungen/)
`€3,50` 100GB
- [Strato](https://www.strato.de/hosting/)
`€4` 3 domains, 1 SSL, 50GB
- [Dogado](https://www.dogado.de/website/hosting)
`€4` 3 domains, 75GB SSD
- [Ionos](https://www.ionos.de/hosting/webhosting)
`€4` 1 domain, 1 SSL, 50GB
- [One](https://www.one.com/de/#PlansAndPrices)
`€4` 1 SSL, 50GB SSD
- [DomainFactory](https://www.df.eu/de/webhosting/)
`€5` 1 SSL, 25 GB
- [Webgo](https://www.webgo.de/ssd-webhosting/)
`8€` 3 domains, ∞SSL, 25GB SSD

## 🌳 More complex ways

There are various reasons, why you may end up with a more complicated setup, e.g.:
- You need more compute power, e.g. to handle many requests, a large database, many files, ...
- You want to execute other software, like Node.js, Python, Go, ...
- You want to use some fancy continous deploy (CI) workflow
- The domain shall remain with another provider (e.g. to retain existing email setup)
- The provider of choice doesn’t offer the right hosting or the right domain
- You want to use special services like GitHub pages to host your website
- You want to install a whole environment, e.g. with Docker

### Hosting only providers
You will have to connect an external domain
- [Ueberspace](https://uberspace.de)

### Domain only providers
You will have to connect to an external target host
- [INWX](https://www.inwx.de/de) `€5` .de `€13` .com
- [UnitedDomains](https://www.united-domains.de/domain-registrieren/preisliste/) `19€` .de .com

### Node.js, CI-Deploys, Server-Side-Rendering with JS-Frameworks
When working with static site generators like Hugo, 11ty, Gatsby or JS-Frameworks like Next, Nuxt, Sapper, this kind of hosting can automate and simplify your workflow
- [Begin](https://begin.com) `free`
- [Vercel](https://vercel.com) `free`
- [Netlify](https://www.netlify.com) `free` personal account
- [Ionos Deploy Now](https://www.ionos.de/hosting/deploy-now) `free` public beta

### Static file hosting
When you only need to deliver files as they are (no execution or compute)
- [GitHub Pages](https://pages.github.com) `free`
- [Surge.sh](https://surge.sh) `free`
- [DigitalOcean Spaces](https://www.digitalocean.com/products/spaces/) `€5`

### Linux server
When you need full control and are willing to start with the bare operating system
- [Ionos](https://www.ionos.de/server/vps#tarife) `€1`
- [DigitalOcean Droplet](https://www.digitalocean.com/products/droplets/) `€5`
- [Linode](https://www.linode.com/products/shared/) `€5`

## 💸 Prices
All prices as of April 2021. Products sorted by the cost of the most affordable option. Usually, the price correlates with performance and the quality of the support.

## 📒 Glossary
- **(Web-)Hosting** often means an AMP-instance where you can run code (e.g. PHP) or databases and serve files (read more above)
- **Server** often means a (virtual) computer, that you can configure to your own needs. Of course you can also install a AMP environment to serve your website. But in some cases you will have install all the software yourself.
- **Managed** means that you don’t have to configure the server software yourself via the command line, but the provider offers you a user-interface (e.g. Plesk) to configure the server behaviour and install software
- **Shared, virtual, vServer, VPS** means that you share the physical machine with other customers, which is the most common practice and also consumes less electricity
- **Dedicated** is the opposite of shared, meaning that you alone execute on one physical machine
- **Availability** % of time, the service/machine is accessable from the internet. 99.9% uptime means 45min downtime per month
- **AMP Stack** Apache + MySQL + PHP is the classic website software stack, required for Kirby or Wordpress-websites
- **JAM Stack** JavaScript + API Data + Markup (HTML) is the upcoming software stack, that runs a JS-Framework (Vue, React, Svelte or Angular) both on the server (Node.js) and client side, consumes it’s content from some API and generates HTML from it
- **SSL certificates** are required to show your website via the `https://` protocol. Many providers charge an expensive premium for that, while others offer you unlimited Let’s encrypt certificates. When domain and hosting are seperated, the certificate can be installed both on the domain or on the hosting side.
