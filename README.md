# objective

Deploy pgweb, connecting to an RDS db, behind OAuth

https://github.com/sosedoff/pgweb

https://github.com/pusher/oauth2_proxy

1. Deploy PostreSQL db with fake data from mockaroo.com

2. Apply manifest.yaml

   * Get port pgweb is listening on (8081) out of the dockerfile
   * RDS instance cannot be in the same VPC as the k8s cluster, else you get a DNS error

3. Need to add connection via cmd args

per docs:
```
pgweb --url postgres://user:password@host:port/database?sslmode=[mode]
```
