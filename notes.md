# Managing a custom domain for your GitHub Pages site

https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site

## Configuring an apex domain

To create an A record, point your apex domain to the IP addresses for GitHub Pages.

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

To confirm that your *DNS* record configured correctly, use the dig command, replacing **asumikamikaze.com** with your apex domain. Confirm that the results match the IP addresses for GitHub Pages above.

```bash
dig asumikamikaze.com +noall +answer
~
asumikamikaze.com.	7199	IN	A	216.239.34.21
asumikamikaze.com.	7199	IN	A	204.232.175.78
asumikamikaze.com.	7199	IN	A	216.239.36.21
asumikamikaze.com.	7199	IN	A	216.239.32.21
asumikamikaze.com.	7199	IN	A	216.239.38.21
```

## Configuring a subdomain

Navigate to your DNS provider and create a CNAME record that points your subdomain to the default domain for your site. For example, if you want to use the subdomain www.example.com for your user site, create a CNAME record that points www.example.com to <user>.github.io. For more information about how to create the correct record, see your DNS provider's documentation. For more information about the default domain for your site, see "About GitHub Pages."

To confirm that your DNS record configured correctly, use the dig command, replacing WWW.EXAMPLE.COM with your subdomain.

```bash
dig www.asumikamikaze.com +nostats +nocomments +nocmd
~
www.asumikamikaze.com.	4676	IN	CNAME	asumikamikaze.github.com.
asumikamikaze.github.com. 3599	IN	CNAME	github.github.io.
github.github.io.	3599	IN	A	185.199.108.153
github.github.io.	3599	IN	A	185.199.110.153
github.github.io.	3599	IN	A	185.199.109.153
github.github.io.	3599	IN	A	185.199.111.153
```
