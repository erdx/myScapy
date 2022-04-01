SCAPY KURULUM :
pip install scapy

ÇALIŞTIRMA:
sudo scapy

MEVCUT PROTOKOLLER:
ls()

TÜM KOMUTLAR LİSTESİ:
lsc()

PCAP DOSYA OKUMA:
pkt=rdpcap("/data/ornek.pcap")


UYGUN ALANLARI LISTELE:
dir(IP)
dir(TCP)
dir(ICMP)
dir(Ether)

PAKET OLUŞTURMA:
ip=IP(src="192.168.1.2")

PAKET ALANI DEĞİŞTİRME:
ip.dst="192.168.1.1"

PAKETİ GÖSTERME:
ip.show()

IP PAKETİNE TCP SEGMENTI EKLEME:
ip=IP(src="192.168.1.2", dst="192.168.1.1")
tcp=TCP(sport=1025, dport=80)
(tcp/ip).show()

dot1Q ETHERNET FRAMES:
Ether()/Dot1Q()/IP()

IEEE 802.11
Dot11()/IP()


PAKET GÖNDERME (LAYER3):
send(ip/tcp)

PAKET GÖNDERME (LAYER2):
sendp(Ether()/ip/tcp)


PAKET GÖNDERME ve ALMA (send receive = sr):
sr()

TEK PAKET GÖNDERME:
ip=IP(dst='test.deneme.com')
pkt=ip/ICMP()
sr(pkt)

ÇOKLU PAKET GÖNDERME / ALMA:
ip=IP(dst='test.deneme.com')
pkt=ip/ICMP()
srloop(pkt, count=3)

TEK PORT TARAMA:
ip=IP(dst="test.com.tr")
tcp=TCP(dport=80,flags="S")
sr1(ip/tcp)

PORT ARALIĞI TARAMA:
ip=IP(dst='test.deneme.com')
tcp=TCP(sport=666, dport=(440,443), flags="S")
sr(ip/tcp)






