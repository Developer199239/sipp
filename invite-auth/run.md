sipp -i 192.168.0.106 -sf ./invite-auth.xml -inf ./invite-accounts.csv 192.168.0.114:5060 -r 1 -rp 1000 -trace_err

** for single call**
sipp -i 192.168.0.106 -sf ./invite-auth.xml -inf ./invite-accounts.csv 192.168.0.114:5060 -m 1 -trace_err
