
# Deploying nemanode (Zhen lab specific)

What you need:
1. ssh access to the <LINUX_SERVER>

## Updating the client/server

Note: ensure that the server are using has the correct version of node by typing `node --version` (see README for specified node version)

1. ssh to <LINUX_SERVER>
2. cd to <PATH_TO_SERVER_DIR>
3. run `git checkout <GIT VERSION/COMMIT>`
4. configure secrets, port, username, password credentials if any in src/config.js
5. `rm -rf node_modules` if there are dependency changes
6. install dependencies `npm i` if there are dependency changes
7. build the client by running `npm run build-prod`

## Updating the database

8. run `npm run populate-database` if the raw data has changed

## Restarting the server

9. delete the old instance of the server using pm2: `pm2 delete <APP_ID>`
10. restart the server with the new changes: `pm2 start src/server/index.js --cron "*/15 * * * *`