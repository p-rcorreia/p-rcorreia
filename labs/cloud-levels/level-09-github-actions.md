# Level 09 — GitHub Actions com self-hosted runner

**Trilha:** Cloud Levels · Google Cloud / CI/CD  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 09](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloudcomputing-devops-githubactions-activity-7512222191401218048-8tcf)

## Problema

O deploy do Level 08 já era repetível, mas ainda exigia conexão manual à VM para iniciar a atualização.

## Arquitetura usada

`GitHub Actions → self-hosted runner na VM → script de deploy → rsync → Nginx`.

O runner foi instalado na própria VM no Google Cloud. A publicação destaca que ele **inicia uma conexão HTTPS de saída** com o GitHub, sem exigir exposição pública de uma nova porta de entrada ou acesso SSH iniciado pelo GitHub.

## Validação por etapas

1. Primeiro, workflow manual executando apenas `hostname`, `whoami` e `pwd`.
2. Confirmação de que os comandos estavam de fato rodando na VM e no contexto esperado.
3. Execução do script de deploy já criado no Level 08.
4. Ajuste de permissões para evitar dependência de `sudo` interativo.
5. Mudança do acionamento manual para **push na branch main**.
6. Alteração real no site, seguida de publicação sem acesso SSH manual ou execução manual de `git pull` / `rsync`.

## Aprendizado

Workflow, job, step e runner têm responsabilidades diferentes. O resultado foi a passagem de um **deploy repetível** para um **deploy disparado automaticamente**.

**Limite:** o YAML completo do workflow e as permissões do runner não foram reproduzidos na publicação; não são inventados aqui.

[← Índice dos laboratórios](./README.md)
