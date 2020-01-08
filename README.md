# NGinx `sites-available`

[**WEB**](https://tomashubelbauer.github.io/nginx-sites-available)

## Install NGinx

`apt install nginx`

`nginx -t`

## Create a site

`mkdir /var/www/example.com`

`echo example.com > /var/www/example.com/index.html`

`/etc/nginx/sites-available/example.com.conf`:
```nginx
server {
    listen 80;
    listen [::]:80;

    root /var/www/example.com;

    index index.html;

    server_name example.com www.example.com;

    access_log /var/log/nginx/example.com.access.log;
    error_log /var/log/nginx/example.com.error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

`ln -s /etc/nginx/sites-available/bloggo.net.conf /etc/nginx/sites-enabled`

`nginx -t`

`nginx -s reload`

`open example.com`

## Create another site

Repeat the above.

## Subdomain

Use the subdomain in `server_name` and add a subdomain name or wildcard (`*`)
A/AAAA DNS record to the domain's DNS records.
