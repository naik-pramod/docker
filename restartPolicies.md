### Restart Policies
Docker containers does not start when they exit or deamon is restarted.

| Flag        | Description |
| ----------- | ----------- |
| no          | Do not auto restart container       |
| no-failure  | restart if it fails        |
| unless-stopped| restart unless explicitly stopped     |
| always   | Always restart        |