# SPV Install

From https://support.supernet.org/support/solutions/articles/29000016256-komodo-spv-install used for Komodo's fork [Safecoin ](http://safecoin.org/).

Here is a simple installation script for BarterDEX with only electrum coins, no wallets and no blockchains needed.

## Install nanomsg


```
cd

git clone https://github.com/nanomsg/

cd nanomsg

cmake . -DNN_TESTS=OFF -DNN_ENABLE_DOC=OFF

make -j4

sudo make install

sudo ldconfig

```


## Install marketmaker 

```
cd

git clone https://github.com/jl777/SuperNET

cd SuperNET/iguana

git branch spvdex

git checkout spvdex

cd exchanges

./install

cd ../dexscripts

echo "export passphrase=\"`head -c 32 /dev/urandom | base64`\"" > passphrase

chmod 0600 passphrase

./client
``` 

(now a client should be running)

## In a new terminal

```
cd ~/SuperNET/iguana/dexscripts

sudo ./setpassphrase

```
A json file should be opened, check userpass and copy it

Export the pass

```
$ export userpass = "passfromjsonfile"

```
Copy data from http://pad.supernet.org/electrum-servers 

```
sudo nano enable_my
```
Paste it and save the file

Install curl

```
sudo apt-get install curl

```
Finally give permissions and run
```
chmod 755 enable_my
./enable_my
```

Ready, you can now execute commands like ./getcoins ./inventory ./orderbook ./buy and so on


## License

 


