To run a miner or validator in the subnet 27, follow the below given instructions and commands.

Clone the repository of the project and install requirements as:

```
git clone https://github.com/neuralinternet/compute-subnet.git
cd compute-subnet
python3 -m pip install -r requirements.txt
pyhton3 -m pip install -e .
```

Before moving forward you need to have wallet (Cold Key) and Hot key:

```
btcli  w new_coldkey
btcli w new_hotkey
```



Now, you need TAO in your wallet (coldkey) for registration.

For registration of the hotkey run:

```
btcli s register --subtensor.network finney --netuid 27
```

Before running or validator you need to have `pm2` installed, install it using:
 

```
sudo apt update
sudo apt install npm
sudo npm install pm2 -g
```


You need Docker too, install going through this link (https://docs.docker.com/engine/install/ubuntu/).


Now, using `pm2` run `miner` as:

```
pm2 start neurons/miner.py --name MINER --interpreter python3 -- --netuid 27 --wallet.name COLDKEY --wallet.hotkey HOTKEY --axon.port AXON-PORT --logging.trace --logging.debug --subtensor.network finney 

```


To run a `validator` use:

```
pm2 start neurons/validator.py --name Validator --interpreter python3 -- --netuid 27 --wallet.name COLDKEY --wallet.hotkey HOTKEY --axon.port AXON-PORT --logging.trace --logging.debug --subtensor.network finney 

```

After launching miner/validator you can then check the logs as:

```
pm2 logs 

```

Good Luck!
