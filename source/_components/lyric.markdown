---
layout: page
title: "Honeywell Lyric"
description: "Instructions how to integrate Honeywell Lyric into Home Assistant."
date: 2017-01-25 21:22
sidebar: true
comments: false
sharing: true
footer: true
logo: lyric.png
ha_category: Hub
featured: false
---

The Lyric component is the main component to integrate all [Lyric](http://lyric.honeywell.com/) related platforms. To connect Lyric, you will have to [sign up for a developer account](http://developer.honeywell.com/) and get a client_id and client_secret.

### {% linkable_title Setting up developer account %}

1. Visit [Honeywell Developers](http://developer.honeywell.com/), and sign in. Create an account if you don't have one already.
2. Fill in account details.
3. Submit changes
4. Click "[My Apps](http://developer.honeywell.com/user/me/apps)" at top of page, under your account.
5. Click "[Create New App](http://developer.honeywell.com/user/me/apps/add)"
6. Fill in details:
  - App name. We recommend somthing with Home Assistant.
  - In the "Callback URL" enter the adress to your Home Assistant instance: "https://yourhomeassistant:8123/api/lyric/authenticate". If you have base_url in your http config, use this url. Otherwise use your local ip.
7. Click "Save Changes"
8. On the apps page, click on the just created app.
9. The "Consumer Key" and "Consumer Secret" are shown now. These will be used as `client_id` and `client_secret` below.
10. Once Home Assistant is started, a configurator will pop up asking you to log into your Lyric account.

### {% linkable_title Configuration %}

```yaml
# Example configuration.yaml entry
lyric:
  client_id: CLIENT_ID
  client_secret: CLIENT_SECRET
```

```yaml
# Example configuration.yaml entry to show only devices at your vacation and primary homes
lyric:
  client_id: CLIENT_ID
  client_secret: CLIENT_SECRET
  locations:
    - Vacation
    - Primary
```

Configuration variables:

- **client_id** (*Required*): Your Lyric developer client id.
- **client_secret** (*Required*): Your Lyric developer client secret.
- **locations** (*Optional*): The location or locations you would like to include devices from. If not specified, this will include all locations in your Lyric account.