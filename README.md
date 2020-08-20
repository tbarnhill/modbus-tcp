# modbus-tcp-ip
A simple interface for Modbus over TCP/IP
* Read and write modbus registers
* Support for promises and callbacks 


# Quick Example
``` javascript
const modbus = require('modbus-tcp-ip')
const device = modbus(ipAddress,port,unitId)

//Read
let myCoil = await device.read('c0')
let myHoldingRegister = await device.read('hr0') 
let myHoldingRegisters = await device.read('hr1-2') 

//Write
await device.write('c0',true)
await device.write('hr0',15)

```

# Device Object 
## Constructor 
``` javascript
const modbus = require('modbus-tcp-ip')
const device = modbus(ipAddress,port,unitId)
```


## Properties 

* ipAddress
* port
* unitId
* timeout
* online 

## Methods

### read(address,[callback])
* address - Coil or register to read. 
* callback(err,res) - Optional.

### write(address,value,[callback])
* address - Coil or register to read. 
* value - Data to write. 
* callback(err,res) - Optional.




# Address Syntax
[Short Hand + Register Number]

##### i.e.
* 'i8'        - Descrite Input 8
* 'hr418'     - Holding Register 418 
* 'hr418-419' - Holding Registers 418 through 419

##### Applicable Datatypes
```
Data Type                  Short Hand   Size        Accessibility     
Descrite Input             i            1 Bit       Read Only
Coil                       c            1 Bit       Read / Write
Input Register             ir           16 Bits     Read Only
Holding Register           hr           16 Bits     Read / Write
```
# Implemented Function Codes
* FC1 - Read Coil
* FC2 - Read Input
* FC3 - Read Holding Registers
* FC4 - Read Input Registers
* FC5 - Write Single Coil
* FC6 - Write Single Register
* FC15 - Write Multiple Coils
* FC16 - Write Multiple Registers






