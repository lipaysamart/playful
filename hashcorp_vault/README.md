## Hashcorp Vault

## Todo

- Prepared
- Start
- Initialize Vault
- Login

### Prepared

- docker
- docker-compose
- A domain
- Self signed certificate

### Start

```sh
docker compose up -d
```

### Initialize Vault

- Login to vault (https://vault.docker.local:8200)

首次设置时，会看到以下内容，用于创建我们的初始根密钥，并指定它应该拆分为多少个共享，以及需要提供多少个共享才能恢复它 [Shamir's secret sharing](https://en.wikipedia.org/wiki/Shamir%27s_secret_sharing)

![vault initialize](./assets/vault-initialize.png)

- Download keys

- Unseal Vault

输入文件中的任意两个 `.keys` 解封 `vault`
![unseal vault](./assets/unseal-vault.png)

### Login

来到登陆界面后使用 Token 登陆
![login](./assets/login.png)

## Conclusion

至此使用 `docker` 部署`Hashicorp Vault` 已经完成，可以开始使用啦。

## Tips

- 生成自签名证书

```sh
docker run --rm -it -e CERT_CN=homelab -v `pwd`/tls:/ssl registry.cn-shenzhen.aliyuncs.com/lipaysam/certs-maker:v3.6.1 "--CERT_DNS=*.docker.local"
```

## Reference

- [What is Vault](https://developer.hashicorp.com/vault/docs/what-is-vault)
- [Programster blog](https://blog.programster.org/deploy-hashicorp-vault-through-docker)
- [Why vault needs the IPC_LOCK !](https://stackoverflow.com/questions/50031086/why-does-vault-by-hashicorp-require-the-ipc-lock-capability-to-be-enabled)