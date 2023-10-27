+++
title = 'Update and thoughts on FOSS'
date = 2023-10-26T22:44:53+08:00
description = "Recent FOSS experiments and thoughts"
tags = [
    "markdown",
    "css",
    "html",
    "hugo",
]
categories = [
    "Open-Source",
    "Fair-Code",
]
draft = false
+++
It's a crunch period at work these days and have very little time for studies and hobbies...

# Thoughts
I use **open-source** because it's lightweight and runs well on my Raspberry Pi. I don't think the **commercial** server will run on a Pi. I have not used the **commercial** server, so I can't really make a meaningful comparison.

On the subject of whether it's OK to trust **open-source** over **commercial**, I've followed the discussions in this thread with interest and would like to share my views. Whatever trust we invest in open-source software can certainly be [exploited](http://social.technet.microsoft.com/wiki/contents/articles/13383.best-practices-for-page-file-and-minimum-drive-size-for-os-partition-on-windows-servers.aspx). In the same way, a rogue developer could inject malicious code into a non-commercial project, a rogue employee could inject malicious code into a commercial project. Being linked to a company is no guarantee that the product can be trusted, open-source or not. It isn't a matter of trusting any one developer or company, but trusting that all the cogs in the open-source machinery are turning to make the open-source model work. The real question is, how much do we trust that robust steps are being taken to mitigate the risk of such exploits?

With open-source software, anyone can perform an audit to check that there is no malicious code. With smaller projects like **vaultwarden**, we know the code can be audited in full, we just don't know who has done it, when and how, if at all. In most small hobbyist projects, a systematic, independent code audit most certainly never happens, and we mostly just trust that if anything was amiss, somebody else would have spotted it. The problem is, we are all that somebody else. On the other hand, **Bitwarden** pays a third-party auditor for their code to be independently audited, and they publish their [audit reports for the world to see](https://bitwarden.com/help/article/is-bitwarden-audited/). This is one step that **Bitwarden** has taken to earn our trust that most smaller projects like **vaultwarden** cannot afford.

This is not to say never trust small non-commercial projects. There are other ways smaller projects can earn our trust. I personally look for projects with multiple contributors who also contribute to other reputable projects, look at how the developers respond to issues in the issue tracker, the quality of their documentation, and even just the history of how the project came about. All these can give an indication of developer motivation and diligence in making sure that the code is clean.

Whilst companies need to earn our trust because they want us to use their software so they can make money, smaller non-commercial/hobbyist projects may not necessarily care whether we do or not. In such cases, the developers may well be trustworthy but may not be incentivized enough to demonstrate the same level of commitment to earning our trust. To be fair, the onus is not on them to convince us to use their software, but on us to decide how much we're willing to trust them for the convenience of using their software. It's worth remembering this when choosing where to place our trust.

**Counterpoint to this:** their incentive to (even deceptively) maintain trust and profit can easily lead to hiding known security issues and (unbeknownst to us) using plaintext/low-quality encryption of data.

# Recent Deployed Projects
- [CloudPanel](https://www.cloudpanel.io/): Basic cPanel alternative for Wordpress deployments, but of course, Wordpress is bloated so go [Hugo](https://gohugo.io/) for efficiency and security if you don't mind posting with markdowns
- [SerpBear](https://docs.serpbear.com/): Free Serp tracking for SEO related works
- [Uptime Kuma](https://uptime.kuma.pet/): Uptime monitor that is pretty famous these days
- [Wazuh](https://wazuh.com/): Free Splunk SIEM alternative, but do check out SecurityOnion as well
- [tldfraw](https://www.tldraw.com/): Diagraming tool for simple work
- [Excalidraw](https://plus.excalidraw.com/): Diagraming tool for complex work
- [Upptime](https://github.com/jiannystein/upptime): Uptime monitor using only Github Actions, no server required
- [VaultWarden](https://www.vaultwarden.net/): Password Manager

# Freebies
## Docker
I typically favor Docker deployments because they efficiently manage dependencies. The commands are easy to work with, you either `docker compose` a customizable YAML file or `docker run -d --restart=always -p <ServerPort>:<DockerPort> -v <source:version>` on any projects that support Docker deployments

## Cloudflare Tunnel
Additionally, the free Cloudflare Tunnel greatly simplifies proxy management by establishing an encrypted tunnel between the origin server and the nearest Cloudflare data center, all without the need to expose any public inbound ports on the server. This setup not only shields the origin server against DDoS attacks and data breach attempts but also enhances security. However, the decision of whether to entrust Cloudflare with your traffic is a subjective one, as it may no longer remain entirely private.

In summary, if you lack expertise in securing your connections, opting for Cloudflare Tunnel can be a safer and more convenient choice, achieved with just a few clicks. It's important to note that using this service involves the decryption of all SSL-encrypted connections by Cloudflare, which means that connection data briefly exists on their servers in plain text before being re-encrypted for transport to users.

## Cloudflare Page Rules
For admin login pages of these seldom-used open-source projects that you may not regularly monitor, Cloudflare's free tier provides 3 Page Rules. You can utilize these Page Rules to enable the "Browser Integrity Check" and set the Security Level to "I'm Under Attack" in order to safeguard against bots and crawlers.