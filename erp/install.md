---
title: Install OpenG2P ERP
description: Installing ERP
keywords: openg2p, installation, install, OpenG2P ERP

---

## Supported platforms

OpenG2P ERP runs on any platform that supports docker. See the docker documentation for the list of [supported platforms](https://docs.openg2p.com/ee/supported-platforms)

## Installation Methods

The ERP can be installed either by: 1) running the docker image we provide, or 2) from source using our repo. You can always contact us for [help](https://openg2p/contact).

<ul class="nav nav-tabs">
  <li class="active"><a data-toggle="tab" href="#installdocker">Docker</a></li>
  <li><a data-toggle="tab" href="#installsource">From Source</a></li>
</ul>
<div class="tab-content">
  <div id="installdocker" class="tab-pane fade in active">
{% capture installdocker-content %}

### Docker

#### Installing

We provide a docker image and docker compose that gets you up and running and is the easiest and recommended installation method. It does require you to have docker running on the target machine and know your way around docker; see the [docker documentation](https://docs.docker.com/get-started/).

```bash
git clone git@github.com:OpenG2P/openg2p-erp-docker.git openg2p-erp
cd openg2p-erp
```

These files must be present before you run `docker-compose`:

- `./.docker/odoo.env` must define `ADMIN_PASSWORD` an administrative password for managing your ERP instance.
- `./.docker/db-access.env` must define `PGPASSWORD` password to your postgres database and should be equal to `POSTGRES_PASSWORD` below.
- `./.docker/db-creation.env` must define `POSTGRES_PASSWORD` (must be equal to `PGPASSWORD` above).

Use the provided example docker-example folder and set your passwords as explained above. Passwords should be random, and secure.

```bash
mv dot-docker-example .docker
```

#### Booting

Once these secret files are in place start the reverse proxy that boots [traefik](https://docs.traefik.io/).

```bash
docker-compose -p inverseproxy -f inverseproxy-none-ssl.yaml up -d
```

>**Note**: There is an SSL variant inverseproxy-ssl.yaml that is recommended when not running behind an SSL enabled gateway. This needs documenting

Then start up `docker-compose`.

```bash
docker-compose -f prod.yaml up -d
```

If installing for the first time, you will need to initialize the database

```bash
docker-compose run --rm odoo odoo --stop-after-init -i openg2p
```

Finally point your browser to http://your-domain and log in with the default credentials:

username: `admin`
password: `admin`


> Change your password immediately after [login](./guide/configuration.md#changing-the-admin-password)!
>
{: .warning}

{% endcapture %}
{{ installdocker-content | markdownify }}

</div>
<div id="installsource" class="tab-pane fade" markdown="1">
{% capture installsource-content %}

### From Source

OpenG2P ERP is a set of addons extending Odoo to provide the functionalities necessary to managing large scale transfer programs. Consequently, it can be installed like any Odoo addon. However that needs some familiarity with installing and managing Odoo deployments that is outside the scope of this documentation.

To get started grap the [OpenG2P ERP Addon Repo](https://github.com/openg2p/openg2p-erp-addons); we have also curated a list of community addons we depend on [here](https://github.com/openg2p/openg2p-erp-community-addons).

{% endcapture %}
{{ installsource-content | markdownify }}
</div>
<hr>
</div>


## Where to go next

- [Intial configuration](guide/configuration)
- [Learn how to use the ERP](guide)
- [Using in production](production)
- [Learn how to extend the ERP](exending)
