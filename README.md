# Self Hosted Notabase

This repository demonstrates how to self host your own [Notabase](https://notabase.io/) instance.

Simply run `docker compose up` to start a nextjs container running Notabase as well as the required [Supabase](https://supabase.com/docs/guides/self-hosting) containers.

`docker compose` requires a `.env` file to be present in the root folder. An example can be found in `.env.local.example`. You can `cp` this file and adjust the values to your needs.

Please don't deploy this to an unprotected server (enable secure communication and configure your firewall first). Your data may not be secure. Use at your own risk. 

Notabase is licensed under the AGPL license, and is free for personal use.

If you'd like to use Notabase for commercial use, please contact [Richard Chu
](https://github.com/churichard) for a commercial license.

## Change to a different Notabase version

1. update your `.env` file and set `NOTABASE_DOWNLOAD_URL` to the corresponding download url:

    ```
    NOTABASE_DOWNLOAD_URL=https://github.com/churichard/notabase/archive/[commit_hash].tar.gz
    ```

2. re-build the frontend image:

    ```
    docker compose build frontend --no-cache
    ```
