## how to setup local dev env for hyperLedger

- Login into Huawei cloud, go to blockchain service
- Follow the [official document](https://support.huaweicloud.com/bestpractice-bcs/bcs_bestpractice1_0004.html) to download 
certificates. Copy and unzip the certificates in `resources/fabric` folder
- Set the file name of admin private key:`fabricAdminPrivateKeyFileName` in `config.proterties`.The file
 admin private key file is in `fabric/peer/msp/keystore`
- Edit you hosts file(`/etc/hosts` on linux/MacOS, `C:\Windows\system32\drivers\etc\hosts` on windows),
to add(update IP and host if changed):
```
117.78.39.82 peer-4428b63567b14b99db5ebb50d254b06e895c7aeb-0.peer-4428b63567b14b99db5ebb50d254b06e895c7aeb.default.svc.cluster.local
117.78.39.82 orderer-3c0590126a6d4cb3aff24f854f92329b265c36cd-0.orderer-3c0590126a6d4cb3aff24f854f92329b265c36cd.default.svc.cluster.local
```
- start JFinal


## how to run the chaincode locally.


To run chaincode locally outside kcoin, just follow:
- Setup $GOPATH, `$HOME/go`
- Follow official document to download and build Fabric locally
- Follow https://hyperledger-fabric.readthedocs.io/en/release-1.2/chaincode4ade.html to setup dev mode


And for kcoin:
```
cd <your fabric-samples dir>
mkdir chaincode/kcoin
cp <kcoin_repo_root>/src/server/src/main/resources/chaincode/kctoken.go chaincode/kcoin/
cd chaincode-docker-devmode
```
Then open 3 terminals on that folder

#### terminal 1
```
docker-compose -f docker-compose-simple.yaml up
```
Note that sometimes container `cli` will fill to start, you need to rm it first.

#### terminal 2
```
docker exec -it chaincode bash
cd kcoin
go build
CORE_PEER_ADDRESS=peer:7052 CORE_CHAINCODE_ID_NAME=kcoin:1.0 ./kcoin
```

#### terminal 3
```
docker exec -it cli bash
peer chaincode install -p chaincodedev/chaincode/kcoin -n kcoin -v 1.0
peer chaincode instantiate -n kcoin -v 1.0 -c '{"Args":["0"]}' -C myc


# create new token
peer chaincode invoke -n kcoin -c '{"Args":["initLedger", "symbol", "name", "owner", "10000"]}' -C myc
# query balance
peer chaincode query -n kcoin -c '{"Args":["balance", "symbol", "owner"]}' -C myc
# transfer
peer chaincode invoke -n kcoin -c '{"Args":["transfer", "symbol", "owner", "user1", "10"]}' -C myc
# query again
peer chaincode query -n kcoin -c '{"Args":["balance", "symbol", "owner"]}' -C myc
peer chaincode query -n kcoin -c '{"Args":["balance", "symbol", "user1"]}' -C myc

# query history
peer chaincode query -n kcoin -c '{"Args":["historyQuery", "symbol"]}' -C myc

```