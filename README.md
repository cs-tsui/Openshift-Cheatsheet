# Openshift-Cheatsheet

Approve CSR

```
oc get csr -o name | sed -e 's/.*\///g' | xargs -I {} oc adm certificate approve {}
```

Print out global pull secret
```
oc get secret pull-secret -n openshift-config -o yaml -o jsonpath='{.data.\.dockerconfigjson}' | base64 -d |jq
```
