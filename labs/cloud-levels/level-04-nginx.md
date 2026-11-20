# Level 04 — Nginx, HTTP e troubleshooting

**Trilha:** Cloud Levels · Google Cloud / Linux  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 04](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_googlecloud-nginx-linux-activity-7510873346192945153-mpGL)

## Pergunta do laboratório

O que muda quando um site deixa de depender de um servidor HTTP temporário executado manualmente e passa a ser entregue pelo Nginx, como serviço do sistema operacional?

## Ambiente e percurso

A publicação descreve a substituição do servidor Python temporário pelo Nginx em uma VM. O serviço passou a escutar a porta 80, permitindo acesso HTTP sem acrescentar `:8000` ao endereço. A página inicial padrão foi localizada em `/var/www/html` e substituída pelo site do Cloud Levels.

## Validações relatadas

- Requisição para a página principal: `GET / 200` no `access.log`.
- Caminho inexistente: resposta `404`.
- Arquivo sem permissão de leitura: resposta `403 Forbidden` e indicação de `Permission denied` no `error.log`.
- Com o Nginx interrompido por `systemctl`, o IP e a regra de firewall permaneceram, mas o site ficou indisponível por ausência de processo escutando a porta.

## Decisão e aprendizado

O Nginx foi tratado não apenas como “um servidor web”, mas como serviço Linux, processo, listener HTTP, servidor de arquivos e fonte de logs. A rotina de alteração ficou: **editar configuração → validar com `nginx -t` → aplicar com reload**.

**Limite desta documentação:** o post não publica a configuração completa do Nginx nem evidências em arquivos reutilizáveis. Este documento registra o experimento relatado; não finge conter um script reproduzível completo.

[← Índice dos laboratórios](./README.md)
