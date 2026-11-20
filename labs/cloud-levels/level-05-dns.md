# Level 05 — DNS, IP estático e diagnóstico por camadas

**Trilha:** Cloud Levels · Google Cloud / DNS  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 05](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_googlecloud-dns-nginx-activity-7511085466645921792-zTae)

## Problema

O site já respondia pelo endereço IPv4 público da VM, mas precisava responder pelo domínio **cloudlevels.com.br**.

## Configurações descritas

- Registro **A** para o domínio raiz, apontando ao IPv4 da VM.
- Registro **CNAME** de `www.cloudlevels.com.br` para `cloudlevels.com.br`.
- Reserva de um **IP público estático**, em substituição ao endereço efêmero.

Fluxo conceitual: `domínio → DNS → IP da VM → Nginx → site`.

## Incidente real

O DNS respondia, o Nginx estava ativo, havia processo escutando na porta 80, o `localhost` retornava HTTP 200 e o firewall estava correto. Mesmo assim, a página pelo domínio não abria.

**Causa identificada:** o registro A ainda apontava para o IP anterior, enquanto a VM já utilizava o IP estático. Após atualizar o registro e aguardar a propagação, o domínio passou a funcionar.

## Insight de arquitetura

`api.cloudlevels.com.br` e `cloudlevels.com.br/api` têm implicações distintas: o primeiro é um nome DNS, potencialmente associado a outra infraestrutura; o segundo é um caminho HTTP interpretado depois da resolução do nome.

**Aprendizado central:** isolar a camada defeituosa antes de alterar configurações indiscriminadamente.

[← Índice dos laboratórios](./README.md)
