# Exc5

Создание выделенного namespace:

```bash
kubectl create namespace exc5-namespace
```

Развёртывание pod'ов для тестирования сетевого policy с указанием меток:

```bash
kubectl run front-end-app --image=nginx --labels=role=front-end --expose --port=80 -n exc5-namespace
kubectl run back-end-api-app --image=nginx --labels=role=back-end-api --expose --port=80 -n exc5-namespace
kubectl run admin-front-end-app --image=nginx --labels=role=admin-front-end --expose --port=80 -n exc5-namespace
kubectl run admin-back-end-api-app --image=nginx --labels=role=admin-back-end-api --expose --port=80 -n exc5-namespace
```

Применение сетевых policy:

```bash
kubectl apply -f non-admin-api-allow.yaml
kubectl apply -f admin-api-allow.yaml
```