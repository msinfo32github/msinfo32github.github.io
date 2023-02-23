---
title: How to read news quicker (using RSS!)
date: 2023-02-20 20:30:00 +0100
categories: [rss,news]
tags: [rss,news,homelab]
---

Most news sites now are ad-filled, and even with an ad-blocker are full of a lot of javascript, bloating the websites. This makes it almost impossible to read actual content.

## How can you fix this?

Most websites actually have an [RSS feed](https://en.wikipedia.org/wiki/RSS), allowing you to read content through an RSS reader. Most websites typically hide RSS feeds but they are easily able to be found using browser extensions such as Get RSS Feed URL, which is available for [FireFox](https://addons.mozilla.org/en-GB/firefox/addon/get-rss-feed-url/) and [Google Chrome](https://chrome.google.com/webstore/detail/get-rss-feed-url/kfghpdldaipanmkhfpdcjglncmilendn?hl=en)

## FreshRSS

FreshRSS is [a free, self-hosted feeds aggregator](https://freshrss.org/) that is open-source, and available to self-host.

It can be installed using docker very easily. You can either install using the official instructions from the [FreshRSS GitHub](https://github.com/FreshRSS/FreshRSS#installation) or using [LinuxServer.io's](https://linuxserver.io/) docker container.

It can be installed using LinuxServer's docker container following their official guide.

## FreshRSS Setup

You can setup FreshRSS using a `docker-compose.yml` file.

Run the following commands to create this file and start FreshRSS.

```bash
nano docker-compose.yml
```

Input this into the file:

```yml
---
version: "2.1"
services:
  freshrss:
    image: lscr.io/linuxserver/freshrss:latest
    container_name: freshrss
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /path/to/data:/config
    ports:
      - 80:80
    restart: unless-stopped
```

(This Docker Compose file may change at any point, and it is recommended to use the most up to date version [here](https://hub.docker.com/r/linuxserver/freshrss) under the Usage tab)

Exit out of nano using `CTRL+S`, and `CTRL+X` to save and exit. You can now run the docker-compose by running:

```bash
docker-compose up
```

(This may require sudo!)

Navigate to http://SERVER_IP:80/ and you will now see this:

![fresh-rss-step-01](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-01.png)

Select your preferred language and click `Submit`.

![fresh-rss-step-02](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-02.png)

Scroll down and click `Go to the next step`.

![fresh-rss-step-03](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-03.png)

Select your database type and click `Submit`.

![fresh-rss-step-04](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-04.png)

Input a username, authentication method and password and click `Submit`.

![fresh-rss-step-05](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-05.png)

Congrats! You have now configured FreshRSS. Click `Complete installation` and you will be redirected.

![fresh-rss-step-06](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-06.png)

Input your username and password, and click `Login`.

![fresh-rss-step-07](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-07.png)

You will now see the UI of FreshRSS, with the default subscription of FreshRSS releases. Click on the `Subscription management` button.

![fresh-rss-step-08](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-08.png)

You can now see all subscriptions to RSS feeds. You can categorize them, remove and add feeds here.

## FreshRSS theming

You can theme FreshRSS by clicking the `Settings Cog` in the top right of the screen, and clicking on `Display` under `Configuration`.

![fresh-rss-step-09](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-09.png)

You can now select themes by sliding through the themes available and clicking `Save` to save changes. I personally like the `Nord` theme as seen below.

![fresh-rss-step-10](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-10.png)

## How to add RSS feeds

You can find RSS feeds from websites by installing an addon above. I use [Get RSS Feed URL](https://addons.mozilla.org/en-GB/firefox/addon/get-rss-feed-url/).

Visit a site, and click on the addon to see a page like this.

![fresh-rss-step-11](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-11.png)

You can now click the Copy URL button and input this into FreshRSS under a new subscription.

![fresh-rss-step-12](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-12.png)

Adding a subscription allows you to change the title, description and website URL. Click `Submit` when you are finished.

![fresh-rss-step-13](/assets/img/2023-02-20-how-read-news-quicker/fresh-rss-step-13.png)

On the FreshRSS feed you will now be able to read posts from this website, as can be seen above.

## Mobile Apps

Many mobile apps exist, such as Readrops, FeedMe, EasyRSS, Fluent Reader Lite and more can be seen on this list [here](https://github.com/FreshRSS/FreshRSS#apis--native-apps).

I personally use Readrops which has a great UI, with dark theme. It can easily connect to a FreshRSS instance.

![readrops](/assets/img/2023-02-20-how-read-news-quicker/readrops.png)

## Conclusion

You are now complete, with a RSS Feed and are able to view it from Desktop, and Mobile. This is a much better way to consume online content without distractions and the slowing down from modern websites.

If there are any further tweaks or any issues, leave them under my GitHub issues [here](https://github.com/msinfo32github/msinfo32github.github.io/issues/) or in the comment section below!