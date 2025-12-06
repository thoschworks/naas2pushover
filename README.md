# ❌ naas2pushover – Sending out rejection reasons from No-as-a-Service via Pushover.net

`naas2pushover` is a shell script that fetches a random, generic, creative, and sometimes hilarious rejection reason from the service [no-as-a-service](https://github.com/hotheadhacker/no-as-a-service) and distributes it via [Pushover.net](https://pushover.net). Currently, the use of the API endpoint https://naas.isalman.dev/ is  hardcoded.

## Prerequisites
* A Unix-like system with internet access to run the script.
* An account at [Pushover.net](https://pushover.net).
* An application registered at Pushover.net with its corresponding API key.
* A Delivery Group set up at Pushover.net. This allows forwarding to multiple people.  
Even when used by only one person, I recommend using a delivery group, as it is easier to clean up in case of a data leak than the user key.

## Configuration
Configuration is managed via environment variables. Currently, the two variables below are defined:

| Variable                         | Function                                                     |
| -------------------------------- | ------------------------------------------------------------ |
| NAAS2PUSHOVER_PUSHOVER_API_TOKEN | Enter the API key of the registered application              |
| NAAS2PUSHOVER_PUSHOVER_USER_KEY  | Enter the Delievery Group key or the User Key (not recommended) |

The script is designed to be used with `cron`. You can define the variables in the crontab using `crontab -e`:

```
NAAS2PUSHOVER_PUSHOVER_API_TOKEN="your_api_token_here"
NAAS2PUSHOVER_PUSHOVER_USER_KEY="your_user_key_here"

# m h  dom mon dow   command
*/5 * * * *  /path/to/naas2pushover
```

## Debugging and Development

For debugging and development, copy the file `sample.env` to `.env` and populate it with the correct values. Sourcing `. .env` will load those environment variables into the current shell.

In debug mode — enabled by setting the environment variable `DEBUG=1` — certain states are logged to the console.

```shell
DEBUG=1 ./naas2pushover
```

## Disclaimer

The script's foundational structure was produced using a Large Language Model (aka AI). I reviewed the functionality and subsequently refined and extended it manually.