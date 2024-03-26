# k8s

## Quickstart

You will need `helm` installed. On MacOS, you can do this with:

```bash
brew install helm
```

Next, run:
```bash
make init # Adds and installs key helm repos

kubectl apply -f namespaces.yaml # Adds namespaces
kubectl apply -f production_issuer.yaml # Adds LetsEncrypt TLS cert issuer
kubectl apply -f volumes.yaml # Adds PersistentVolumeClaims and PersistentVolumes

# Optional - update volumes' reclaim policies to 'Retain'
make retain pv=$PV_NAME # Run this for each volume
```

For rolling deployments:
```bash
kubectl rollout restart deployment/<deployment> -n <namespace>
```

## [thecodeboss.dev](https://thecodeboss.dev)

Services: 1 (frontend)
Includes: Deployment, Service, Ingresses

To Deploy:
```bash
kubectl apply -f thecodeboss
```

## [simpleslides.dev](https://simpleslides.dev)

Services: 3 (app, db, redis)
Includes: Deployments, Services, Ingresses, Secrets, and Volume

To Deploy:
```bash
cp simple-slides/secrets.yaml.example simple-slides/secrets.yaml
# Add in your secrets to simple-slides/secrets.yaml

kubectl apply -f simple-slides
```

## [websockets.thecodeboss.dev](https://websockets.thecodeboss.dev)

Services: 2 (frontend & backend)
Includes: Deployment, Service, and Ingress

To Deploy:
```bash
kubectl apply -f websockets
```
