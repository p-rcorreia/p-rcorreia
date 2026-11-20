# Level 08 — Deploy com Git, SSH e rsync

**Trilha:** Cloud Levels · Linux / Git / Deployment  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 08](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_cloudcomputing-devops-git-activity-7512169393590521857-O2OI)

## Desafio

O processo anterior dependia de cópias manuais com `scp` e `cp`. O objetivo era tornar o deploy **organizado e reproduzível**, antes de automatizá-lo.

## Implementação relatada

- Instalação de Git na VM.
- Geração de uma **Deploy Key SSH dedicada**, com acesso somente de leitura ao repositório, sem reutilizar a chave pessoal.
- Separação do diretório de código versionado (`~/repos/cloud-levels`) do diretório publicado pelo Nginx (`/var/www/cloud-levels`).
- Sincronização com **rsync**; o uso de `--delete` foi estudado para alinhar o destino à origem.
- Consolidação do processo num script `~/bin/deploy-cloud-levels`.

O fluxo descrito foi: `git push → GitHub → git pull na VM → rsync → Nginx`.

## Validações

A publicação relata validação de `index.html`, CSS, JavaScript, HTTPS e da interface do projeto em produção.

## Lições

**Git não é deploy:** enviar alterações ao GitHub, por si só, não altera os arquivos servidos pelo Nginx. A evolução foi de cópia manual para um comando repetível, deixando a automação contínua para o próximo nível.

**Cuidado:** os comandos aqui ilustram a sequência publicada; não incluem as opções completas do `rsync` nem o script original.

[← Índice dos laboratórios](./README.md)
