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

## Map a path and download intel files
```bash
docker run -v /tmp/intel:/opt/critical-stack/frameworks/intel darendarrow/critical-stack-intel-client:0.0.4 /sbin/my_init --skip-startup-files --quiet -- /usr/bin/critical-stack-intel --api-key=XXXXXX pull
critical-stack 22:19:02 [ERROR] --- NOTICE ----------
critical-stack 22:19:02 [ERROR] Unable to locate bro or configure permissions properly.
critical-stack 22:19:02 [ERROR] Unable to add sudoers access for bro binary.
critical-stack 22:19:02 [INFO] If you have a custom setup you can add your paths manually.
critical-stack 22:19:02 [INFO] $ sudo critical-stack-intel config --set bro.path=/my/path/bro
critical-stack 22:19:02 [INFO] $ sudo critical-stack-intel config --set bro.include.path=/my/path/local.bro
critical-stack 22:19:02 [INFO] $ sudo critical-stack-intel config --set bro.broctl.path=/my/path/broctl
critical-stack 22:19:02 [ERROR] --- NOTICE ----------
critical-stack 22:19:02 [INFO] Pulling feed list from the Intel Marketplace.
critical-stack 22:19:03 [INFO] Downloading feed information. Run with the `--debug` flag for more information.
7 / 7  100.00 % 3s
critical-stack 22:19:06 [INFO] Creating master file: master-public.bro.dat. Please wait.
critical-stack 22:19:07 [INFO] Master file created successfully.
critical-stack 22:19:07 [INFO] Intel files located at: /opt/critical-stack/frameworks/intel
critical-stack 22:19:07 [INFO] API Requests Remaining: 996 of 1000/minute
```

The files will be stored in /tmp/intel if you use this example.
