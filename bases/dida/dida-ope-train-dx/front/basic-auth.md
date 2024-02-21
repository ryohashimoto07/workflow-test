# Memo for nginx-ingress basic auth

- [guide](https://kubernetes.github.io/ingress-nginx/examples/auth/basic/)

## create secret

```sh
kubectl create secret generic basic-auth-ope-train-dx --from-file=bases/dida/dida-ope-train-dx/front/auth
```

## add member

安全性高い[bcrypt](https://httpd.apache.org/docs/2.4/misc/password_encryptions.html)を使用すること

```sh
htpasswd -B auth {username}
# or
htpasswd -nbB {username} {password}
```

## remove member

- delete record from `./auth`
- delete and recreate secret
  - `kubectl delete secret basic-auth-ope-train-dx`
