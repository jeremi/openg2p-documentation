---
title: "Orientation and Setup"
keywords: get started, setup, orientation, quickstart, intro, concepts, openg2p
description: Get oriented on some basics of OpenG2P and install OpenG2P.
---

{% include_relative nav.html selected="1" %}

Welcome! We are excited that you want to learn OpenG2P. The OpenG2P Quickstart teaches you how to:

** Set up OpenG2P (on this page) **

<!-- 2.  [Initial Configuration](part2.md)

3.  [Deploying to Production](part3.md) -->

## Set up

<ul class="nav nav-tabs">
  <li class="active"><a data-toggle="tab" href="#installdocker">Docker</a></li>
  <li><a data-toggle="tab" href="#installsource">From Source</a></li>
</ul>
<div class="tab-content">
  <div id="installdocker" class="tab-pane fade in active">
{% capture installdocker-content %}

### Docker

#### Steps :
You can grab the official docker image of odoo(12.0) :

<https://hub.docker.com/_/odoo>

Clone OpenG2P repository :

<https://github.com/OpenG2P/openg2p-erp>

Clone OpenG2P-community-addon repository : 

<https://github.com/OpenG2P/openg2p-erp-community-addon>

Mount OpenG2P-odoo addons within the Odoo container, at /mnt/extra-addons : 

`(sudo)docker run -v /path/to/addons:/mnt/extra-addons -p 8069:8069 -v odoo-db:/var/lib/postgresql/data -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -e  
POSTGRES_DB=postgres --name db postgres:13 --name odoo --link db:db -t odoo`

Access ERP at port `localhost:8069`.

{% endcapture %}
{{ installdocker-content | markdownify }}

</div>
<div id="installsource" class="tab-pane fade" markdown="1">
{% capture installsource-content %}

### From Source
Follow steps on official odoo documentation : 

<https://www.odoo.com/documentation/12.0/administration/install.html#:~:text=systemctl%20start%20odoo-,Source%20Install,-The%20source%20%E2%80%9Cinstallation>

Clone OpenG2P repository :

<https://github.com/OpenG2P/openg2p-erp>

Clone OpenG2P-community-addon repository : 

<https://github.com/OpenG2P/openg2p-erp-community-addon>

Paste them inside odoo directory.

Install requirements file inside virtual environment :

`pip install -r requirements.txt`

Start ERP using the command : 

`python odoo-bin -r {username} -w {password}  
--addons-path=addons,openg2p-erp,openg2p-erp-community-addon -d {database_name}`


{% endcapture %}
{{ installsource-content | markdownify }}
</div>
<hr>
</div>


## Conclusion

At this point, you've installed OpenG2P.

<!-- [On to Part 2 >>](part2.md){: class="button outline-btn" style="margin-bottom: 30px; margin-right: 100%"} -->

