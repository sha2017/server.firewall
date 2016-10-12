iptables__:
   policy: 
     input:   "ACCEPT"
     forward: "ACCEPT"
     output:  "ACCEPT"

   v4:
     nat:
       - name: "Source NAT Rule"
         chain: "POSTROUTING"
         jump: "SNAT"
         source: "10.0.1.11"
         to_source: "94.142.241.115" 

       - name: "Destination NAT Rule"
         chain: "PREROUTING"
         jump: "DNAT"
         destination: "94.142.241.115" 
         to_destination: "10.0.1.11"

       - name: "Output NAT Rule"
         chain: "OUTPUT"
         jump: "DNAT"
         destination: "94.142.241.115" 
         to_destination: "10.0.1.11"

     filter:
       - name: "ALLOW SSH"
         chain: "INPUT"
         jump: "ACCEPT"
         protocol: "tcp"
         dst_port: "22"
   v6: 
     nat:
     filter: