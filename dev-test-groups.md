## create key,csr,crt for developer team
# for u in murali mohan asad danika astosh; do openssl genrsa -out $u.key 2048; openssl req -new -key $u.key -out $u.csr -subj "/CN=$u/O=developer"; sudo openssl x509 -req -in $u.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out $u.crt -days 365; kubectl config set-credentials $u --client-certificate=$u.crt --client-key=$u.key; kubectl config set-context $u-context --cluster=kubernetes --user=$u; done
---
## create key,csr,crt for tester team
# for u in likitha pavithra; do openssl genrsa -out $u.key 2048; openssl req -new -key $u.key -out $u.csr -subj "/CN=$u/O=tester"; sudo openssl x509 -req -in $u.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out $u.crt -days 365; kubectl config set-credentials $u --client-certificate=$u.crt --client-key=$u.key; kubectl config set-context $u-context --cluster=kubernetes --user=$u; done

## see every users group
# for f in *.crt; do openssl x509 -in "$f" -noout -subject; done
