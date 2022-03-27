# 🦦 traefik 优先级

为避免路径重叠，默认情况下，使用规则长度按降序对路线进行排序。优先级直接等于规则的长度，所以最长的长度优先级最高。

优先级 = 0 表示使用默认规则长度排序。

## 🕹️ 使用优先级
``` yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: default-page
  namespace: traefik
  annotations:
    traefik.ingress.kubernetes.io/router.priority: "1"
spec:
  rules:
    - host: "*.yourdomain.xx"
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: yourservice
                port:
                  number: 80
```

这里配置优先级为 ```1``` 及最低优先级。