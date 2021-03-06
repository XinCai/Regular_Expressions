# Regular_Expressions
Regular Expressions (regex) tutorial

如何理解 kubernetes nginx ingress 中的 annotation `nginx.ingress.kubernetes.io/rewrite-target` 

[rewrite target 原文](https://kubernetes.github.io/ingress-nginx/examples/rewrite/#rewrite-target "rewrite target")

## Create an Ingress rule with a rewrite annotation:

```
$ echo '
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$2
  name: rewrite
  namespace: default
spec:
  rules:
  - host: rewrite.bar.com
    http:
      paths:
      - backend:
          serviceName: http-svc
          servicePort: 80
        path: /something(/|$)(.*)
' | kubectl create -f -
```

In this ingress definition, any characters captured by (.*) will be assigned to the placeholder $2, which is then used as a parameter in the rewrite-target annotation.

For example, the ingress definition above will result in the following rewrites:
- `rewrite.bar.com/something` rewrites to `rewrite.bar.com/`
- `rewrite.bar.com/something/` rewrites to `rewrite.bar.com/`
- `rewrite.bar.com/something/new` rewrites to `rewrite.bar.com/new`

[Captured groups](https://www.regular-expressions.info/refcapture.html "Captured groups") are saved in numbered placeholders, chronologically, in the form $1, $2 ... $n. These placeholders can be used as parameters in the rewrite-target annotation.

### 如何测试 K8s 的 Nginx Ingress 

Check if the contents of the annotation are present in the nginx.conf file using: `kubectl exec ingress-nginx-controller-873061567-4n3k2 -n kube-system -- cat /etc/nginx/nginx.conf` 
