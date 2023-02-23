---
title: How to setup local reverse proxy with Pi-Hole and NGINX
date: 2023-02-20 18:30:00 +0100
categories: [dns,reverse proxy]
tags: [dns,reverse proxy,homelab,networking]
---

Are you tired of typing IP addresses & ports all the time? I was, so I setup a [**reverse proxy**](https://www.cloudflare.com/en-gb/learning/cdn/glossary/reverse-proxy/) to allow me to type a local domain instead!

# How?

For my setup it's pretty easy, especially if you already have ProxMox setup

I use Pi-Hole as my DNS server, which you can setup very easily with [this](https://tteck.github.io/Proxmox/) nifty ProxMox script (under Ad Blocker - DNS, Pi-hole LXC) or manually using the official guide [here](https://docs.pi-hole.net/main/basic-install/)

After you have setup PiHole, you can now install NGINX, this can be within an LXC, VM or however else you would like (as long as you can access the configuration files). Using a ProxMox LXC running Debian Linux, you can install it by running this command:

## Required installs

NGINX is obviously required, and can be installed on most debian-based systems using:

```bash
sudo apt install nginx
```

## NGINX Configuration

After installation, navigate to the default configuration file at `/etc/nginx/sites-available/`

You can edit this with:

```bash
nano default
```

Removing all lines within the default configuration file you can then add each service you would like to reverse proxy

An example of this is a basic reverse proxy to [Jellyfin](https://jellyfin.org/), this can be done with this configuration:

```yaml
server{
    listen 80;
    server_name jellyfin.lan;

    location / {
        proxy_pass "http://192.168.0.200:8096";
    }
}
```

Obviously, this will not work if your Jellyfin is not on the port above. You can also replace the .lan address to any address, although it is most recommended to use non-existant TLDs, such as .lan or .arpa

In some cases, you may require extra configuration to allow proxying of a service, an example of this can be with [TVHeadEnd](https://tvheadend.org/) I solve this by adding the extra lines seen here:

```yaml
server{
        listen 80;
        server_name tvheadend.lan;

        location / {
                proxy_pass http://192.168.0.151:9981;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "upgrade";
        }
}
```

## Pi-Hole Configuration

With your Pi-Hole installed, navigate to `Local DNS` and `DNS Records`. You will now want to add your service you added using configuration above. 

For the `Domain` field, you can input the `server_name` used within the NGINX configuration. For `IP Address` you need to input the IP address of your NGINX server.

## Conclusion

After setting your client devices of Pi-Hole to your DNS server, you should now be able to access your services you have setup through the `server_name` you have set.

If this does not work, try troubleshooting by:

- Checking if you are using Static IPs
- Check Pi-Hole logs to see if your device is using it
- Check if your device overrides custom DNS servers (typically done within smart TVs)

With a Pi-Hole server setup, you can also now use it for ad-blocking, using Adlists from [Firebog](https://firebog.net/)!

If there are any further tweaks or any issues, leave them under my GitHub issues [here](https://github.com/msinfo32github/msinfo32github.github.io/issues/) or in the comment section below!