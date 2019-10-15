INTRODUCTION
=======
This manual will tell you how to run your own cybex node as a non-witness.

ENVIRONMENT
======
Cybex non-witness node can be run on linux distribution like Ubuntu. You may use the latest version of your distribution.
If you run it on X86_64 platform with Linux, you can use our prebuilt programs. Several easy steps need to be taken before you bring up the node.
However, if you do not have X86_64 Linux environment to run your own non-witness node, you may build it from source.

INSTALL PREBUILT PROGRAMS (on X86_64 Linux)
======
Step1. Build your own working directory. We will refer it as $CYBEX_ROOT_DIR in this document.
```Bash
export CYBEX_ROOT_DIR=${PATH TO YOUR NEWLY BUILT DIRECTORY}
```

Step2. Build sub-directories.
```Bash
cd $CYBEX_ROOT_DIR
mkdir bin
mkdir data
```
Step3. Download prebuilt witness_node, cli_wallet to bin directory, 
```Bash
wget https://github.com/CybexDEX/how-to-run-cybex-node/raw/master/bin/witness_node -O bin/witness_node
wget https://github.com/CybexDEX/how-to-run-cybex-node/raw/master/bin/cli_wallet -O bin/cli_wallet
md5sum witness_node # will output "df5fe64df21bf1d26a6264da8e51f0a1 witness_node"
md5sum cli_wallet # will output "9edbecfb5c37fad3381ccb66572027ff  cli_wallet"
```

Step4. Download genesis.json, config.ini

If you want to connect to **TEST** chain
```Bash
cd $CYBEX_ROOT_DIR
wget https://raw.githubusercontent.com/CybexDEX/how-to-run-cybex-node/master/testchain/genesis.json -O genesis.json
wget https://raw.githubusercontent.com/CybexDEX/how-to-run-cybex-node/master/testchain/config.ini -O data/config.ini
```

If you want to connect to **MAIN** chain
```Bash
cd $CYBEX_ROOT_DIR
wget https://raw.githubusercontent.com/CybexDEX/how-to-run-cybex-node/master/mainchain/genesis.json -O genesis.json
wget https://raw.githubusercontent.com/CybexDEX/how-to-run-cybex-node/master/mainchain/config.ini -O data/config.ini
```

Sometimes you may need to set execute bit to binary
```Bash
cd $CYBEX_ROOT_DIR
chmod u+x bin/cli_wallet bin/witness_node
```

Step5. Start non witness-node
```Bash
cd $CYBEX_ROOT_DIR
./bin/witness_node -d data --genesis-json genesis.json --max-ops-per-account 500 --resync-blockchain --replay-blockchain
```


**Attention**

If you use macOS, please replace the witness_node with this:

```Bash
wget https://github.com/CybexDEX/how-to-run-cybex-node/raw/master/mac-bin/witness_node -O bin/witness_node
wget https://github.com/CybexDEX/how-to-run-cybex-node/raw/master/mac-bin/cli_wallet -O bin/cli_wallet
```

Check sum of binary
```Bash
$ md5sum witness_node
c8929ef1c61c8f060785552c2b059fd4   witness_node
534faa2613003a2b842554c0aacdf692   cli_wallet
```
