# Openshift-Cheatsheet

Approve CSR

```
oc get csr -o name | sed -e 's/.*\///g' | xargs -I {} oc adm certificate approve {}
```
