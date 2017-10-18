# hyperledger-chaincode-test

## start chaincode devmode
```
git clone https://github.com/hyperledger/fabric-samples.git

cd chaincode-docker-devmode

docker-compose -f docker-compose-simple.yaml up
```

## install command line tools

```
curl -sSL https://goo.gl/Q3YRTi | bash
export PATH=<path to download location>/bin:$PATH
```

## build chaincode

```
cd $CHAINCODE_DIR
go get -u --tags nopkcs11 github.com/hyperledger/fabric/core/chaincode/shim
go get -u --tags nopkcs11 github.com/hyperledger/fabric/protos/peer
go get -u --tags nopkcs11 github.com/op/go-logging
go build --tags nopkcs11
```

## start chain-code

```
CORE_PEER_ADDRESS=localhost:7051 CORE_CHAINCODE_ID_NAME=chaincode-test:0 ./chaincode-test
```

## install chain-code

```
peer chaincode install -p ./ -n chaincode-test -v 0
```

## instantiate chain-code

```
peer chaincode instantiate -n chaincode-test -v 0 -c '{"Args":[]}' -C myc
```

## invoke chain-code

```
peer chaincode invoke -n chaincode-test -v 0 -c '{"Args":["1000.00","cristiano","341-4864-051353","2019-10-10"], "Function" : "register_payment"}' -C myc
```

## query chain-code
```
peer chaincode query -n chaincode-test -v 0 -c '{"Args":["341-4864-051353"], "Function" : "payment_details"}' -C myc
```

