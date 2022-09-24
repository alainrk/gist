# Cron

## Run script as cron
- Useful way to debug cronjob failures without waiting for cron to execute it, with the ease of manual execution and using the cron context
- Create a cron entry to extract your cron environment (save cron env in you home)
  ```sh
  crontab -e
  # Add * * * * * /usr/bin/env > /home/<username>/cron-env
  ```
  - Save
  - Remember to remove it or run it every X minutes/hours/days.
- Create a wrapper
  - Create run-as-cron.sh
    ```sh
    #!/bin/sh

    . "$1"
    exec /usr/bin/env -i "$SHELL" -c ". $1; $2"
    ```
  - `chmod +x run-as-cron.sh` and potentially set it in $PATH.
- Run the original cron script as it was ran by cron itself
  - `run-as-cron ~/cron-env 'cronscript.sh'`
  - Debug without waiting for cron to execute it