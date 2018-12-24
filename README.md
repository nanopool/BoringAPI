# BoringAPI
# version: 1.0
BoringAPI can be used to retrieve stats from a running instance of **nanominer** (or any other miner) which has an active monitoring port (for **nanominer** it is specified by the "port" config option and defaults to 9090). To get the stats, send a HTTP GET request to the BoringAPI server, for example http://127.0.0.1:9090/stats. This is an example of a response for a rig with 5 GPUs, 3 of them are mining Ethash, the other 2 are mining CryptoNightV8, also with RandomHash being mined on the CPU:

```json
{  
   "Algorithms":[  
      {  
         "CryptoNightV8":{  
            "CurrentPool":"xmr-eu1.nanopool.org:14444",
            "GPU 1":{  
               "Accepted":2,
               "Denied":0,
               "Hashrate":"2.040000e+02"
            },
            "GPU 3":{  
               "Accepted":4,
               "Denied":0,
               "Hashrate":"1.990000e+02"
            },
            "ReconnectionCount":0,
            "Total":{  
               "Accepted":6,
               "Denied":0,
               "Hashrate":"4.030000e+02"
            }
         },
         "Ethash":{  
            "CurrentPool":"eth-eu1.nanopool.org:9999",
            "GPU 0":{  
               "Accepted":3,
               "Denied":0,
               "Hashrate":"2.040000e+07"
            },
            "GPU 2":{  
               "Accepted":2,
               "Denied":0,
               "Hashrate":"2.020000e+07"
            },
            "GPU 4":{  
               "Accepted":5,
               "Denied":0,
               "Hashrate":"1.970000e+07"
            },
            "ReconnectionCount":0,
            "Total":{  
               "Accepted":10,
               "Denied":0,
               "Hashrate":"6.030000e+07"
            }
         },
         "RandomHash":{  
            "CPU":{  
               "Accepted":6,
               "Denied":6,
               "Hashrate":"1.980000e+02"
            },
            "CurrentPool":"pasc-eu1.nanopool.org:15556",
            "ReconnectionCount":0,
            "Total":{  
               "Accepted":6,
               "Denied":6,
               "Hashrate":"1.980000e+02"
            }
         }
      }
   ],
   "Devices":[  
      {  
         "CPU":{  
            "Name":"Intel(R) Core(TM) i5-7400 CPU @ 3.00GHz",
            "Platform":"CPU"
         },
         "GPU 0":{  
            "Name":"P106-100",
            "Platform":"CUDA",
            "Pci":"01:00.0",
            "Fan":48,
            "Temperature":65,
            "Power": 104.3
         },
         "GPU 1":{  
            "Name":"RX 550",
            "Platform":"OpenCL",
            "Pci":"02:00.0",
            "Fan":48,
            "Temperature":62,
            "Power": 104.3
         },
         "GPU 2":{  
            "Name":"P106-100",
            "Platform":"CUDA",
            "Pci":"03:00.0",
            "Fan":48,
            "Temperature":62,
            "Power": 104.3
         },
         "GPU 3":{  
            "Name":"RX 550",
            "Platform":"OpenCL",
            "Pci":"04:00.0",
            "Fan":48,
            "Temperature":59,
            "Power": 104.3
         },
         "GPU 4":{  
            "Name":"P106-100",
            "Platform":"CUDA",
            "Pci":"05:00.0",
            "Fan":48,
            "Temperature":59,
            "Power": 104.3
         }
      }
   ],
   "WorkTime":143
}
```
This API uses the following measure units:
* Hashrate - Hashes/Solutions per second;
* Fan - percentage;
* Temperature - Celsius degrees;
* Power - watts;
* WorkTime - seconds.

The "PCI" field uses Bus:Device.Function notation (https://wiki.xen.org/wiki/Bus:Device.Function_(BDF)_Notation).
