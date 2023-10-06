ChicagoCrashes
==============

Python scripts and n8n workflow to scrape and process data from: https://crash.chicagopolice.org

Credentials
------------

[n8n](https://n8n.io/) dashboard accessible via plaintext HTTP on port 5678. 

Frontail (https://github.com/mthenw/frontail) instances 
to monitor scraping and data export are available on port 9002 and 9003.

Credentials:

* Username: `user`
* Password: `HYOfbhgA6MpUJpEXgbHULfTw`

Twilio and SendGrid credentials can be configured in .ini files.

Vagrant can be used to launch the entire system inside VM. Terraform can be used to create and provision VPS on
Digital Ocean. There is also a Terraform config file to provision proxy servers (proxies.tf) with a helper script
(setup_proxies.py). Note that you need to import n8n workflow from ChicagoCrashesV2.json into n8n server and enable it
via n8n web interface.

[Dolt](https://github.com/dolthub/dolt) is used for version-controlable database by scraper and other script.

CLI of scraper
--------------

```
usage: scrape.py [-h] --dolt-db-dir DOLT_DB_DIR [--try-next TRY_NEXT] [--try-prev TRY_PREV] [--force-start-rd FORCE_START_RD] [--yesterday] [--disable-proxies]

optional arguments:
  -h, --help            show this help message and exit
  --dolt-db-dir DOLT_DB_DIR
                        directory for Dolt DB
  --try-next TRY_NEXT   number of RDs to try after last known one
  --try-prev TRY_PREV   number of RDs to try before last known one
  --force-start-rd FORCE_START_RD
                        explicit value of initial RD
  --yesterday           use reference RD from yesterdays data
  --disable-proxies     disable proxies
```
