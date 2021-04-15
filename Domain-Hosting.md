# Domain & Hosting

A **website** and a **domain** are two different things: The **website is a collection** of files that can be rendered by your browser. These files are stored on some **server**, a computer that is always connected to the internet and which can be accessed by "calling" it’s **IP address**. And then there is a domain, which redirects your request to that servers IP address. Because on one server with one IP address, there can be multiple websites, the domain is also used by the server to determine which directory of files should be delivered.

## The easy way

The easiest is to have domain, email and webhosting with one provider. Many providers call this product "webhosting", and often there is almost nothing that can go wrong:
- Buy a webhosting package and select an available domain
- Create an FTP user and upload your website to the webspace
- Go to domain settings and direct the website to that directory where you uploaded the website
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

### Providers
Some providers that offer as-easy-as-possible webhosting:
- [Dogado](https://www.dogado.de/website/hosting)
- [DomainFactory](https://www.df.eu/de/webhosting/)
- [Hetzner](https://www.hetzner.com/de/webhosting)
- [HostEurope](https://www.hosteurope.de/webhosting-loesungen/)
- [Ionos](https://www.ionos.de/hosting/webhosting)
- [One](https://www.one.com/de/#PlansAndPrices)
- [Netcup](https://www.netcup.de/hosting/)
- [Velogrid](https://www.velogrid.com/)
- [Webgo](https://www.webgo.de/ssd-webhosting/)

## More complex ways

There are various reasons, why you may end up with a more complicated setup, e.g.:
- You need more compute power, e.g. to handle many requests, a large database, many files, ...
- You want to execute other software, like Node.js, Python, Go, ...
- You want to use some fancy continous deploy (CI) workflow
- The domain shall remain with another provider (e.g. to retain existing email setup)
- The provider of choice doesn’t offer the right hosting or the right domain
- You want to use special services like GitHub pages to host your website
- You want to install a whole environment with Docker

### Hosting only providers
- [Ueberspace](https://uberspace.de)

### Domain only providers
- [UnitedDomains](https://www.united-domains.de/domain-registrieren/preisliste/)
- [INWX](https://www.inwx.de/de)

### Node.js, CI-Deploys, Server-Side-Rendering with JS-Frameworks
- [Netlify](https://www.netlify.com)
- [Vercel](https://vercel.com)
- [Begin](https://begin.com)
- [Ionos Deploy Now](https://www.ionos.de/hosting/deploy-now)

### Static file hosting
- [GitHub Pages](https://pages.github.com)
- [Surge.sh](https://surge.sh)
- [DigitalOcean Spaces](https://www.digitalocean.com/products/spaces/)

### Linux server
- [DigitalOcean Droplet](https://www.digitalocean.com/products/droplets/)
- [Linode](https://www.linode.com/products/shared/)
- [Ionos](https://www.ionos.de/server/vps#tarife)

## Glossary
- **Managed** means that you don’t have to configure the server software yourself via the command line, but the provider offers you a User-Interface to configure the server behaviour.
- **Shared** means that you share the physical machine with other customers, which is the most common practice and also consumes less electricity.
- **Dedicated** is the opposite of shared, meaning that you alone execute on your machine.
- **Virtual Sever (vServer/VPS)** is a shared server, that feels like a dedicated server offering you full control over the operating system. But still you share the physical machine.

## Email

coming...
