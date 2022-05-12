# Running API Gateway on Azure AKS

## Create Kubernetes Namespace

```bash
kubectl create namespace test
```
kubectl create secret docker-registry regcred \
    --docker-server=docker-registry.demo.axway.com/apim-demo \
    --docker-username='robot$rathna' \
    --docker-password="eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NTQ0NTAwNTcsImlhdCI6MTY0NjY3NDA1NywiaXNzIjoiaGFyYm9yLXRva2VuLWRlZmF1bHRJc3N1ZXIiLCJpZCI6NjIsInBpZCI6NCwiYWNjZXNzIjpbeyJSZXNvdXJjZSI6Ii9wcm9qZWN0LzQvcmVwb3NpdG9yeSIsIkFjdGlvbiI6InB1c2giLCJFZmZlY3QiOiIifSx7IlJlc291cmNlIjoiL3Byb2plY3QvNC9oZWxtLWNoYXJ0IiwiQWN0aW9uIjoicmVhZCIsIkVmZmVjdCI6IiJ9LHsiUmVzb3VyY2UiOiIvcHJvamVjdC80L2hlbG0tY2hhcnQtdmVyc2lvbiIsIkFjdGlvbiI6ImNyZWF0ZSIsIkVmZmVjdCI6IiJ9XX0.XcUt_kzSjqEVoFNR5Esil4L4Pco9QjXcAyqf7j7tBKYnaBkNntb68w7vrwfkIQhoo5sPndra-BVFJvxNHmg2FzEPvgZ7Gk98864KUUghzPQCZ1UDJH5gjUbqg5o-lUh0mXT62uKH30mdte3wN1V6EGu2gxR3wOGWgNZsVt-uIDWBOmWldWD4vJobr5BpqIPqEppKnsme7a9YgbEf75UY4UcVi4WpxX0i98WfTZCER6nQhVXfVQHLxzxhGfwY8tBf1ZtTa3Ju6nCD26bdEuY2_n94NJoTxAtbQ9Q61Lv0T-Eb9p87YEqvNR9BlcV6PHMIhnUv5hrQIKjCPE4thr4n9GtQh_k6eb40oTasWgZMHbKUs8Lax7GAZMc7gYF9BSUefcDqqNJHcKajeFmM7MAvJLaENCTPoWfKj70D0j2_oKZyhYm5kSKVG6zPzFiG2CM0ysBby5dFepXEgokMiUyTTm-_DcPhPzQ4wfFBb7Tgh2o_oDORKgw2sCkrAwkxTlACF-fH6PVPiL5jE7Utv-PTWItxI5N-t3xcXKQH4ljRCFzO7VqTZWtQAe0AtrCnvSGmAZtlsjQRNjWAU9eFMoHQ6tKiOvu57b0UisVaypCEhM_H9fPmxUMd2qS-UqiZtPSz6_iXTM507T76xK_U9WgNcH9gfoGmjhId9admgaXThAA" \
    --docker-email=demo@axway.com -n test

## Run API Gateway


```bash
kubectl apply -f apigateway.yaml
```


## Run Mysql Gateway


```bash
kubectl apply -f mysql.yaml
```

## Create portal certs as secrets

```bash

kubectl create secret generic apachekey --from-file=apache-selfsigned.key -n test
kubectl create secret generic apachecert --from-file=apache-selfsigned.crt -n test
```

## Run Portal 


```bash
kubectl apply -f apiportal.yaml
```


## Get LB URL

```bash
$kubectl -n test get svc
```

