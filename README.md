# objective

Deploy pgweb, connecting to an RDS db, behind OAuth

https://github.com/sosedoff/pgweb

https://github.com/pusher/oauth2_proxy

1. Deploy PostreSQL db with fake data from mockaroo.com

2. Apply manifest.yaml

   * Get port pgweb is listening on (8081) out of the dockerfile
   * RDS instance cannot be in the same VPC as the k8s cluster, else you get a DNS error

3. Added connection string via cmd args and password in a secret, but fails to authentitcate

per docs:
```
pgweb --url postgres://user:password@host:port/database?sslmode=[mode]
```

   * but it's failing auth
   * K8s isn't parsing the password variable, testing with echo shows it's passing the var name instead of it's contents

4. Create script to run pgweb with connection strings, mount script as configmap volume

5. Set conn strings as 2nd configmap with variables and secret with password, success!


