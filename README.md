<h2>NodeJS SSH2 Command and Control server to launch DDoS attacks using API</h2>

<h3>Coded by forky (tg: ***@yfork***)</h3>


<h1>Installation:</h1>

```sh
curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt -y install nodejs
npm i express
```

<h1>Setup:</h1>

Update servers.json to your servers IP/Ports and names<br>
Update commands.json to your methods names and commands<br>
<h3>Update api.js:</h3><br>

```
const api_port: Your API HTTP Port
const socket_token: Your secret Token for the TCP Socket
const api_key: Your API Key
const domain_lock: true or false (if its set to true you can only access the API if using the domain on api_domain)
```
