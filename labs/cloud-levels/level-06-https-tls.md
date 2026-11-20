# Level 06 — HTTPS, TLS, Certbot e renovação

**Trilha:** Cloud Levels · Google Cloud / Nginx  
**Status:** documentado a partir de laboratório publicado  
**Publicação original:** [LinkedIn — Level 06](https://pt.linkedin.com/posts/paulo-ricardo-correia-533b35244_from-git-to-live-activity-7511179349438586880-F0VG)

## Objetivo

Evoluir o site de HTTP para HTTPS, com certificado válido para o domínio raiz e o `www`.

## Antes da mudança

A publicação registra um teste inicial sem serviço HTTPS na porta 443, sem certificado configurado e sem TLS disponível. O Nginx atendia HTTP pela porta 80, com DNS e IP estático já funcionando.

## Implementação relatada

1. Liberar a porta 443 no firewall.
2. Definir no Nginx os nomes `cloudlevels.com.br` e `www.cloudlevels.com.br`.
3. Utilizar **Certbot / Let's Encrypt** para comprovar o controle do domínio, emitir o certificado e configurar o Nginx.
4. Manter a porta 80 para receber HTTP e redirecionar para HTTPS com resposta **301**.
5. Validar o fluxo com TLS na porta 443.

Fluxo observado: `HTTP → 301 → HTTPS → TLS handshake → GET / → index.html`.

## Validação adicional

A renovação foi simulada com `certbot renew --dry-run`, com sucesso relatado no post.

## Conceito aprendido

O certificado identifica o servidor; ele não representa sozinho todo o HTTPS. A sessão TLS estabelece proteção criptográfica para a comunicação. O arquivo da chave privada não deve ser exposto.

**Limite:** não há cópias de certificados, chaves, arquivos de configuração ou outputs completos neste registro público.

[← Índice dos laboratórios](./README.md)
