simplified object-oriented Python extension module for libpcap - the current tcpdump.org version, the legacy version shipping with some of the BSD operating systems, and the WinPcap port for Windows.

sample usage:

```
>>> import dpkt, pcap
>>> pc = pcap.pcap()
>>> pc.setfilter('icmp')
>>> for ts, pkt in pc:
...     print `dpkt.ethernet.Ethernet(pkt)`
...
Ethernet(src='\x00\x03G\xb2M\xe4', dst='\x00\x03G\x06h\x18', data=IP(src='\n\x00\x01\x1c', dst='\n\x00\x01\x10', sum=39799, len=60, p=1, ttl=128, id=35102, data=ICMP(sum=24667, type=8, data=Echo(id=512, seq=60160, data='abcdefghijklmnopqrstuvwabcdefghi'))))
Ethernet(src='\x00\x03G\x06h\x18', dst='\x00\x03G\xb2M\xe4', data=IP(src='\n\x00\x01\x10', dst='\n\x00\x01\x1c', sum=43697, len=60, p=1, ttl=255, id=64227, data=ICMP(sum=26715, data=Echo(id=512, seq=60160, data='abcdefghijklmnopqrstuvwabcdefghi'))))
^CTraceback (most recent call last):
  File '<stdin>', line 1, in ?
  File 'pcap.pyx', line 298, in pcap.pcap.__next__
KeyboardInterrupt
>>>
>>> pc.stats()
(4851, 0, 0)
```