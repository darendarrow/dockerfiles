# Example usage

## client help
```bash
docker run darendarrow/critical-stack-intel-client:0.0.4 /sbin/my_init --skip-startup-files --quiet -- /usr/bin/critical-stack-intel --api-key=XXXXX --help
usage: critical-stack-intel [<flags>] <command> [<flags>] [<args> ...]

Threat Intel Marketplace client by Critical Stack, Inc

Flags:
  --help              Show help.
  --debug             Enable debug logging.
  -q, --quiet         Remove all output logging.
  --user=USER         Drop privileges to this user.
  --color             Show output color. Default: true
  --api-key=API-KEY   Override stored API key.
  --api-url=API-URL   Override API url.
  --api-version=API-VERSION
                      Override API version. Example: v1
  --global-do-notice  Output master list with do_notice for all indicators.
  --version           Show application version.

Commands:
  help [<command>]
    Show help for a command.

  config [<flags>]
    Configuration management.

  kitty
    Fetch intel sets using your Critical Stack Kitty server.

  list
    List all feeds that belong to your currently set API key.

  api [<flags>] [<api-key>]
    Add or update your API key.

  pull [<flags>]
    Fetch from the Intel market using your API key.

  white-list [<flags>]
    White list configuration management.
```

## List feeds
```bash
docker run darendarrow/critical-stack-intel-client:0.0.4 /sbin/my_init --skip-startup-files --quiet -- /usr/bin/critical-stack-intel --api-key=XXXXX list
critical-stack 19:10:28 [INFO] Pulling feed list from the Intel Marketplace.

   ID  |                           NAME                            | LAST UPDATED | INDICATOR COUNT
+------+-----------------------------------------------------------+--------------+-----------------+
  153  | threatcrowd.org-Community-rated-IP-Blocklist              | -            | 0
  133  | shodan.io-Remote-Access-Trojan-(RAT)-Controllers          | -            | 0
  94   | snort.org-IP-Blacklist                                    | -            | 0
  59   | ET:-Botnet-Command-and-Control                            | -            | 0
  25   | ET:-Known-Compromised-Hosts                               | -            | 0
  23   | Malware-Domains                                           | -            | 0
  18   | PhishTank-Intel-Feed-(Verified)                           | -            | 0
+------+-----------------------------------------------------------+--------------+-----------------+
                                                                        TOTAL     |        0
                                                                   +--------------+-----------------+
<feed-name> = Not Fetched Yet
<feed-name> = On Disk
** = Update Available
`LAST UPDATED` Column = Server time last updated - not local time.
```
