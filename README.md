# Sistema de Vendas — página de divulgação

Landing page do Sistema de Vendas da JN Soluções, publicada pelo GitHub Pages.

**No ar em:** https://joel92246405.github.io/sistema-vendas/

## O que tem aqui

```
index.html   página inteira: HTML + CSS embutido, sem framework
img/         capturas das telas do sistema e a logo
```

Só existe uma dependência externa: a fonte Manrope, pelo Google Fonts.
Sem isso, a página cai numa fonte do sistema e continua legível.

## Publicar uma alteração

```bash
git add .
git commit -m "descrição do que mudou"
git push
```

O GitHub Pages republica sozinho em um ou dois minutos.

## Trocar o instalador da avaliação

O executável **não fica neste repositório** — são 50 MB, e o Git reclama de
arquivo desse tamanho. Ele vai como anexo de *Release*:

1. Em **Releases**, crie uma release nova (ex.: tag `v1.0.1`).
2. Anexe o instalador com o nome exato **`SistemaVendas_Setup_Trial.exe`**.
3. Publique.

Os botões da página apontam para
`/releases/latest/download/SistemaVendas_Setup_Trial.exe`, que sempre entrega o
anexo da release mais recente. Trocar de versão é publicar outra release com o
arquivo usando o mesmo nome — nenhuma alteração na página é necessária.

## Cuidado com os prints

As capturas usam a base de demonstração. A tela de Clientes teve CPF, telefone,
e-mail e endereço substituídos por marcadores (`000.000.000-00`,
`cliente@exemplo.com`) antes de entrar aqui.

**Print novo que mostre dado pessoal passa pelo mesmo tratamento antes de subir.**

## O código-fonte do sistema não está aqui

Este repositório é só a página. O projeto em C# fica fora dele, de propósito.
