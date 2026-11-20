# Level 10.1 — Static at the Edge na AWS

**Trilha:** Cloud Levels · AWS / CDN / CI/CD  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 10.1](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloud-levels-level-101-static-at-the-activity-7512473539397058560--D5T)

## Pergunta

Por que manter uma VM e um Nginx ativos para servir uma aplicação que entrega apenas arquivos estáticos?

## Arquitetura do Kumo, conforme publicada

```text
Vite (build)
    ↓
Amazon S3 (bucket privado)
    ↓ acesso via OAC
Amazon CloudFront (CDN, cache e TLS via ACM)
    ↓
kumo.cloudlevels.com.br
```

O DNS do subdomínio permaneceu no **Registro.br**, segundo a publicação. Assim, não devemos presumir que este laboratório utiliza Route 53.

## Automação

O GitHub Actions passou a executar a publicação a cada push na `main`: instalar dependências, gerar build, autenticar na AWS via **OIDC**, assumir uma **IAM Role com permissões limitadas**, sincronizar `dist/` com o S3 e invalidar o cache do CloudFront.

Um ponto importante foi evitar uma **AWS Access Key permanente armazenada no GitHub**.

## Falha observada

O workflow terminava corretamente e os arquivos do S3 eram atualizados, mas o site ainda exibia a versão anterior. O diagnóstico levou ao cache do CloudFront: a **invalidação** tornou a nova versão disponível.

## Aprendizado

S3, CloudFront, OAC, ACM, IAM, STS, OIDC, cache e GitHub Actions fazem parte de um fluxo de distribuição de aplicações estáticas, não de uma lista desconectada de serviços.

O post encerra o Level 10.1 como concluído e aponta uma comparação futura com Google Cloud; essa comparação não está documentada aqui como realizada.

[← Índice dos laboratórios](./README.md)
