Go HD Wallet tools
------------------

 - BIP32 - https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

###Get this library

        $ go get github.com/WeMeetAgain/gohdwalletutil

###Example

        package main
        
        import (
            "fmt"
            "github.com/WeMeetAgain/gohdwalletutil"
            )
        
        func main() {
            // Generate a random 256 bit seed
            seed,_ := hdwalletutil.GenSeed(256)
            
            // Create a master private key
            masterprv := hdwalletutil.MasterKey(seed)
            
            // Convert a private key to public key
            masterpub := hdwalletutil.PrivToPub(masterprv)
            
            // Generate new child key based on private or public key
            childprv := hdwalletutil.Child(masterprv,0)
            childpub := hdwalletutil.Child(masterpub,0)
            
            // Create bitcoin address from public key
            address := hdwalletutil.PubToAddress(childpub)
            
            _ = childprv
            fmt.Println(address)
        }

###Dependencies

        go get code.google.com/p/go.crypto/ripemd160
        go get github.com/conformal/btcutil
        go get github.com/mndrix/btcutil
