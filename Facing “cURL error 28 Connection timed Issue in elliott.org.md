
### What Error we got 
- I’m getting an error from the Wordpress admin on Elliott.org: “The optin campaign “Elegance Elliott campaign” is failing to convert leads due to the following error “cURL error 28: Connection timed out after 10001 milliseconds”.”

### How we Solve

- We have extende the timeout of this optin campaign to 60 sec instead of 10 sec throught Wp -admin page.
- Add the command 







### How to fix it?

The first thing to do is to update your WordPress to the latest version if not already done.

Then if the problem is still there, contact your hosting company and ask the hosting support team to check the following points :

-   Make sure your server is running a recent version of PHP and the cURL library.
-   Try to increase your [Server Memory Limit settings](https://mailoptin.io/article/fixing-wordpress-customizer-not-loading/#memory).
-   The cURL error can be a DNS related issue. Your hosting company might need to switch DNS configuration to OpenDNS: [https://www.howtogeek.com/164981/how-to-switch-to-opendns-or-google-dns-to-speed-up-web-browsing/](https://www.howtogeek.com/164981/how-to-switch-to-opendns-or-google-dns-to-speed-up-web-browsing/)
-   Ask your host if there is some limitation with wp-cron, or if loopback is disabled.
-   Ask your host if there a firewall or security modules (e.g. mod_security ) that could block the outgoing cURL requests.

You can also install the [Query Monitor](https://wordpress.org/plugins/query-monitor/) plugin and check the status of the HTTP API Calls on the admin page where the error is displayed.

URL of this page: https://mailoptin.io/article/fix-curl-error-28-connection-timed-out-wordpress/

