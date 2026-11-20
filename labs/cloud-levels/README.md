# Cloud Levels — diário de laboratórios

> Da publicação no LinkedIn para uma documentação técnica que possa ser revisitada.

Esta coleção reúne **seis laboratórios documentados a partir de publicações públicas** de Paulo Correia. Cada registro destaca o problema, as configurações relatadas, as validações e os aprendizados. O texto foi reorganizado para consulta no GitHub; **não é um dump integral dos posts nem uma reprodução completa dos arquivos de infraestrutura**.

## Laboratórios documentados

| Level | Experimento | Conceitos principais | Fonte |
| --- | --- | --- | --- |
| [04](./level-04-nginx.md) | Nginx e troubleshooting HTTP | systemd, porta 80, access.log, error.log, 403/404 | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_googlecloud-nginx-linux-activity-7510873346192945153-mpGL) |
| [05](./level-05-dns.md) | DNS e IP estático | Registro A, CNAME, resolução de nomes, diagnóstico | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_googlecloud-dns-nginx-activity-7511085466645921792-zTae) |
| [06](./level-06-https-tls.md) | HTTPS e Certbot | TLS, Let's Encrypt, redirecionamento 301, renovação | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_from-git-to-live-activity-7511179349438586880-F0VG) |
| [08](./level-08-git-ssh-rsync.md) | Deploy manual reproduzível | Git, SSH Deploy Key, rsync, scripts | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloudcomputing-devops-git-activity-7512169393590521857-O2OI) |
| [09](./level-09-github-actions.md) | Deploy automático na VM | self-hosted runner, GitHub Actions, trigger por push | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloudcomputing-devops-githubactions-activity-7512222191401218048-8tcf) |
| [10.1](./level-10-1-aws-static-edge.md) | Static at the Edge na AWS | S3, CloudFront, OAC, ACM, OIDC, CI/CD | [Post](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloud-levels-level-101-static-at-the-activity-7512473539397058560--D5T) |

## Como interpretar este arquivo

- **Documentado** significa que encontrei a publicação original e pude verificar o relato. Não quer dizer que reexecutei o laboratório.
- Os Levels **01–03 e 07** não aparecem neste primeiro conjunto porque não recuperei posts com informações suficientes para documentá-los com a mesma segurança. Isso **não significa** que eles não tenham sido realizados.
- Evitei copiar configurações, IPs, segredos, arquivos privados ou detalhes não publicados.
- Para evidências de execução, diagramas e comandos completos, o ideal é acrescentar arquivos originais sanitizados posteriormente.

## Dois ambientes, duas arquiteturas

**Google Cloud / VM:** Linux → Nginx → DNS → TLS → Git/rsync → GitHub Actions self-hosted.

**AWS / site estático:** Vite → S3 privado → CloudFront/OAC → ACM → GitHub Actions/OIDC.

A comparação entre essas abordagens é um excelente caminho para estudos futuros, mas este índice não atribui conclusões que ainda não tenham sido documentadas.

---

[← Voltar ao perfil](../../README.md) · [LinkedIn](https://www.linkedin.com/in/paulo-ricardo-correia-533b35244/) · [Cloud Levels](https://cloudlevels.com.br)
