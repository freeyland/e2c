# E2C CLI Commands reference

## Project specific

| Command  | Info |
| ------------- | ------------- |
| `e2c add [service] [--help]` | Adds optional service to the project. Available optional services are: elasticsearch, phpmyadmin, rabbitmq and varnish.  |
| `e2c bash [--debug] [--root] ...` | Opens the bash prompt on the project's php Docker service. With --debug flag, the bash prompt will be opened on the project's xdebug Docker service. With --root flag, the root user will be used. |
| `e2c cli [--debug] [--root] ...` | Runs any CLI command without going into the bash prompt of the project's php service. With --debug flag, the CLI command will run on the project's xdebug service. With --root flag, the root user will be used. |
| `e2c db [command] [--help]` | Database related commands. Import/Export database commands and MySQL CLI tool access. Available optional services are: export, import and mysql. Run e2c db --help for command usage information. |
| `e2c down` | Removes project Docker containers, volumes, and networks. Project sources on the host will be untouched. Don't forget to create a database backup before running this command. |
| `e2c grunt` | The grunt command-line interface. Runs grunt specific commands at projects Docker container. Run e2c grunt --help for command usage information. |
| `e2c info` | Prints project info and Docker containers status. |
| `e2c init` | Initializes project in the current directory. Run e2c init --help for command usage information. |
| `e2c down` | Removes project Docker containers, volumes, and networks. Project sources on the host will be untouched. Don't forget to create a database backup before running this command. |
| `e2c m` | Magento command-line tool interface. Runs bin/magento specific commands at projects Docker container. Its is shortened alias of e2c magento command. |
| `e2c mr` | N98-magerun command-line tool interface. Runs n98-magerun specific commands at projects Docker container. It is shortened alias of e2c magerun command. Run e2c mr --help for command usage information. |
| `e2c node`  | Node command-line tool interface. Runs node specific commands at projects Docker container. Run e2c node --help for command usage information. |
| `e2c npm`  | NPM command-line tool interface. Runs npm specific commands at projects Docker container. Run e2c npm --help for command usage information. |
| `e2c redis [options] [cmd [arg [arg ...]]]` | Redis command-line tool interface. Runs redis-cli specific commands at projects Redis Docker container. Run e2c redis --help for command usage information. |
| `e2c remove [service] [--help]`  | Removes optional service from the project. Available optional services are: elasticsearch, phpmyadmin, rabbitmq and varnish. Run e2c remove --help for command usage information. |
| `e2c restart [service [service ...]]` | Restarts running project Docker services and starts all stopped ones. If services explicitly specified, only those will be restarted. |
| `e2c restart [service [service ...]]` | Starts sharing session over ngrok secure tunnels. Command accepts an optional parameter to specify a region. Ex. e2c share eu. Available regions are us, eu, ap, au, sa, jp, and in. By default, region is us. For proper functioning of this command, required dependencies will be installed. Please, visit https://github.com/shkoliar/magento-ngrok and https://github.com/shkoliar/docker-ngrok for more information. Run e2c share --help for command usage information. |

## Gobal

| Command  | Info |
| ------------- | ------------- |
| `e2c global start` | Start the global docker containers: emma2click, mailhog, dnsmasq, portainer, traefik.  |
| `e2c global stop` | Stop the global docker containers.  |
| `e2c global restart` | Restart Emma2click toolset docker services.  |
| `e2c global projects` | Show existing Emma2click-backed projects  |
| `e2c global up` | Create and start Emma2click toolset docker containers, networks and services.  |
| `e2c global update` | Check Emma2click toolset for updates.  |
| `e2c global uninstall` | Uninstall Emma2click toolset from system.  |