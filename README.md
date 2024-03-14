In my environment, I am running k3s on host `k3s.virt` with address `192.168.124.67`. In my `/etc/hosts` file I have:

```
192.168.124.67	k3s.virt whoami-default.example.com whoami-custom.example.com
```

## Configure default certificate

To configure the default certificate:

```
kubectl -n default apply -k default-certificate
```

## Deploy Ingress using default certificate

To deploy a service that relies on the default certificate:

```
kubectl -n default apply -k ingress-with-default-certificate
```

This ingress will be available at `https://whoami-default.example.com`. You will need to update your `/etc/hosts` file appropriately or use curl's `--resolve` option.

## Deploy Ingress using a custom certificate

To deploy a service that uses a custom certificate:

```
kubectl -n default apply -k ingress-with-custom-certificate
```

This ingress will be available at `https://whoami-custom.example.com`. You will need to update your `/etc/hosts` file appropriately or use curl's `--resolve` option.
