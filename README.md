# Blockcast-CLI-Node-Run-Full-Guide
# 🛑🛑 HARDWARE REQ..... 🛑🛑

 # 2 CORE CPU
 # 4 GB RAM
 # 50MBPS INTERNET SPEED 

# Blockcast CLI Node Run Full Guide (PC and VPS)

### Offical Docs Guide - https://docs.blockcast.network/main/getting-started/how-do-i-participate-in-the-network/beacon/start-running-your-beacon-today

----

## 🧰 Prerequisites
### Before getting started, make sure you have the following:
	
Access Platform [HERE](https://app.blockcast.network?referral-code=IIr2Gj)
-------
 * Signup with email on Blockcast
 * Connect ur Phantom Wallet (SOL)
 * Connect ur X (Twitter) and Discord
 * Do Simple quest in profile dashboard

   # 🛑🛑 DOWNLOD DOCKER FIRST 🛑🛑

  🛑🛑  LINK -  https://www.docker.com/products/docker-desktop/

---

1️⃣ Dependencies for WINDOWS & LINUX & VPS
```
sudo apt-get update && sudo apt-get upgrade -y
```
```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```



2️⃣ Clone the Repository
```
git clone https://github.com/Blockcast/beacon-docker-compose.git
cd beacon-docker-compose
```


3️⃣ Start Node
```
docker compose up -d
```

* Note: Before procceding to run node, make sure port `8080` is not in-use. If so, open configuration file with `nano docker-compose.yml` and change the port to `8081` by replacing `8080:8080` with `8081:8080`.

4️⃣ Check Your Containers & Logs
```
docker ps
```
```
docker compose logs -fn 1000
```
skip logs if you have all containers running

5️⃣ Get Hardware ID & Challenge Key
```
docker compose exec blockcastd blockcastd init
```

You'll see output like `Hardware ID: your-hardware-id` and `Challenge Key: your-challenge-key`

6️⃣ Get Location
```
curl -s https://ipinfo.io | jq '.city, .region, .country, .loc'
```

7️⃣ 🛑🛑   Register Your Node 🛑🛑 

* Visit Blockcast Website
* Click the Manage Node and Register Node
* Paste your Hardware ID and Challenge Key and Location
![image](https://github.com/user-attachments/assets/6199c816-d925-414b-b86f-a5a9f3c1c8dd)

SUBMIT AND DONE

## 🛑🛑 For Next Day Run This Command 🛑🛑 

#1 Open WSL and Docker then Put this Command 
```
cd ~/beacon-docker-compose
docker compose up -d
```

## Need to Free Your 8080 Port

### Identify the Process Using Port 8080
```
sudo ss -tulpn | grep 8080
```

Example - ``` LISTEN  0  128  0.0.0.0:0380  0.0.0.0:*  users:(("nginx",pid=1234,fd=6)) ```

### Terminate the Process by PID
```
sudo kill -9 1234
```

### Kill All Processes Using Port 8080
```
sudo fuser -k 8080/tcp
```


## Delete Blockcast node
```
cd /data
docker compose down
rm -rf ~/beacon-docker-compose
```
