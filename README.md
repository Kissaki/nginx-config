Prepared configuration for Nginx.

Managing multiple webpages and subdomains requires some structuring,
and reusing common configuration makes sense.

This setup features some common, reusable configuration (caching, listening…)
in the includes folder, and some sane and safe default configuration for SSL.

sites-available contains an example configuration for a subdomain,
including HTTP to HTTPS rewrite, redirection, and seo-url for some
PHP software.

The example.org is an example configuration featuring various of these,
while the example.com configuration is a minimal configuration.
This makes the latter configuration a good default for new pages,
while the first is a good reference if you are looking to do something
specific.

Now that [Let’s Encrypt](https://letsencrypt.org/) is in open beta, a configuration file
`acme-challenge` is also included to map the challenge url path to
a common location (the challenge is temporary, and has nothing to do
with the actual website).

While some software is not able to handle HTTP and HTTPS at the same
time, since letsencrypt is usable, from now on everything should
be set up to only be served as HTTPS. Thus, HTTP to HTTPS redirection
should be used if it was previously available on HTTP. If not, just
do not provide HTTP at all; browsers will automatically pick up HTTPS.

mime-types was extended; e.g. for json.

The default SSL configuration has been moved out of nginx.conf into includes/ssl.
