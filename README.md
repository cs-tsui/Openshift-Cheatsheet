## Openshift-Cheatsheet

Approve CSR

`oc get csr -o name | sed -e 's/.*\///g' | xargs -I {} oc adm certificate approve {}`


Print out global pull secret

`oc get secret pull-secret -n openshift-config -o yaml -o jsonpath='{.data.\.dockerconfigjson}' | base64 -d | jq`


See trusted CA

`oc get image.config.openshift.io/cluster -o yaml`


Check pull secret on OCP nodes
```
# pull secret on normal cluster
cat /var/lib/kubelet/config.json

# pull secret on ROKS cluster
cat ~/.docker/config.json

# mirror registry file
cat /etc/containers/registries.conf

# trim String - remove first part
echo "delimited.string" | cut -d '.' -f2-
```

Get Ingress Domain

`oc get --namespace=openshift-ingress-operator ingresscontroller/default -o jsonpath='{.status.domain}'`

Add SCC

`oc adm policy add-scc-to-user anyuid -z my-serviceaccount`

## OpenSSL

Show certs on target host/port

`openssl s_client -connect $HOST:$PORT -showcerts`
