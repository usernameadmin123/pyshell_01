!/usr/bin/python3
import sys
from scapy.all import *
 
if len(sys.argv) != 2:
    print("Usage: ./a.py 10.5.98.0")
    print("scan 10.5.98.0/24  find surviving host")
    sys.exit()
sgement_ip=sys.argv[1]
prefix_ip=sgement_ip.split(".")[0]+'.'+sgement_ip.split(".")[1]+'.'+sgement_ip.split(".")[2]+'.'
for addr in range(1,254):
    response=sr1(ARP(pdst=prefix_ip+str(addr)),timeout=0.1,verbose=0)
    try:
        if response != None:
            print(prefix_ip+str(addr))
    except:
        pass
