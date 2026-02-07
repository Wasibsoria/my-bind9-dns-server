Note: The .local warning in the logs is expected. It's
just BIND reminding us that .local is officially for 
multicast DNS. For the sake of this project and local
testing,it doesn't affect performance, but for a real-
world deployment, using a TLD like .home .arpa or .test
would be more pleasant.

vboxuser@defender-ubuntu:~$ dig www.seyit.local

; <<>> DiG 9.18.39-0ubuntu0.24.04.2-Ubuntu <<>> www.seyit.local
;; global options: +cmd
;; Got answer:
;; WARNING: .local is reserved for Multicast DNS
;; You are currently testing what happens when an mDNS query is leaked to DNS
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34791
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: ee1c3817d58e61a20100000069874572bfff070168f3bc1d (good)
;; QUESTION SECTION:
;www.seyit.local.		IN	A

;; ANSWER SECTION:
www.seyit.local.	604800	IN	A	10.0.2.15

;; Query time: 1 msec
;; SERVER: 10.0.2.15#53(10.0.2.15) (UDP)
;; WHEN: Sat Feb 07 17:00:18 +03 2026
;; MSG SIZE  rcvd: 88

vboxuser@defender-ubuntu:~$ dig seyit.local

; <<>> DiG 9.18.39-0ubuntu0.24.04.2-Ubuntu <<>> seyit.local
;; global options: +cmd
;; Got answer:
;; WARNING: .local is reserved for Multicast DNS
;; You are currently testing what happens when an mDNS query is leaked to DNS
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9153
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 646d3afe4963bba5010000006987457f9a9b1c85d0a6426b (good)
;; QUESTION SECTION:
;seyit.local.			IN	A

;; ANSWER SECTION:
seyit.local.		604800	IN	A	10.0.2.15

;; Query time: 1 msec
;; SERVER: 10.0.2.15#53(10.0.2.15) (UDP)
;; WHEN: Sat Feb 07 17:00:31 +03 2026
;; MSG SIZE  rcvd: 84

vboxuser@defender-ubuntu:~$ dig ftp.seyit.local

; <<>> DiG 9.18.39-0ubuntu0.24.04.2-Ubuntu <<>> ftp.seyit.local
;; global options: +cmd
;; Got answer:
;; WARNING: .local is reserved for Multicast DNS
;; You are currently testing what happens when an mDNS query is leaked to DNS
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43562
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 49b15754ee664c830100000069874584feefe8e218ac7b27 (good)
;; QUESTION SECTION:
;ftp.seyit.local.		IN	A

;; ANSWER SECTION:
ftp.seyit.local.	604800	IN	A	10.0.2.15

;; Query time: 1 msec
;; SERVER: 10.0.2.15#53(10.0.2.15) (UDP)
;; WHEN: Sat Feb 07 17:00:36 +03 2026
;; MSG SIZE  rcvd: 88

vboxuser@defender-ubuntu:~$ dig mail.seyit.local

; <<>> DiG 9.18.39-0ubuntu0.24.04.2-Ubuntu <<>> mail.seyit.local
;; global options: +cmd
;; Got answer:
;; WARNING: .local is reserved for Multicast DNS
;; You are currently testing what happens when an mDNS query is leaked to DNS
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45690
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 2278becb2959d4c5010000006987458a49ecaf87795913d5 (good)
;; QUESTION SECTION:
;mail.seyit.local.		IN	A

;; ANSWER SECTION:
mail.seyit.local.	604800	IN	A	10.0.2.15

;; Query time: 0 msec
;; SERVER: 10.0.2.15#53(10.0.2.15) (UDP)
;; WHEN: Sat Feb 07 17:00:42 +03 2026
;; MSG SIZE  rcvd: 89



vboxuser@defender-ubuntu:~$ systemctl status named
● named.service - BIND Domain Name Server
     Loaded: loaded (/usr/lib/systemd/system/named.service; enabled; preset: en>
     Active: active (running) since Sat 2026-02-07 16:31:25 +03; 24min ago
       Docs: man:named(8)
   Main PID: 10658 (named)
     Status: "running"
      Tasks: 8 (limit: 4601)
     Memory: 23.7M (peak: 24.2M)
        CPU: 414ms
     CGroup: /system.slice/named.service
             └─10658 /usr/sbin/named -f -u bind
