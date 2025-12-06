# Consideration

Used instead (or maybe more in complement) of external-dns.  
This [page](https://kubernetes-sigs.github.io/external-dns/v0.14.2/tutorials/ovh/) was followed but without any success. The error encounter was that the pod deployed was not able to see zones or entries :  
```
│ time="2025-09-18T21:06:45Z" level=info msg="OVH: 0 endpoints have been found"
│ time="2025-09-18T21:06:45Z" level=info msg="All records are already up to date"
│ time="2025-09-18T21:07:45Z" level=info msg="OVH: 0 zones found"
```