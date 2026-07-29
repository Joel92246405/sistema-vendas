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

1. Crie a tag antes, senão o campo "Choose a tag" da interface do GitHub
   rejeita o que você digita:

   ```bash
   git tag v1.0.2 && git push origin v1.0.2
   ```

2. Em **Releases** → *Draft a new release*, **selecione a tag na lista**.
3. Anexe o instalador e espere o upload dos 50 MB terminar antes de publicar.
4. **Atualize o nome do arquivo no `index.html`** — são três lugares, todos
   com `SistemaVendas_Setup`: os dois botões e o texto do aviso pós-download.

O link usa `/releases/latest/download/<nome-do-arquivo>`, que sempre entrega o
anexo da release mais recente. Como o nome do arquivo carrega a versão, o passo
4 é obrigatório a cada lançamento.

> Para não precisar do passo 4 nunca mais: anexe **também** uma cópia com nome
> fixo (`SistemaVendas_Setup_Trial.exe`) e aponte a página para ela. Aí trocar
> de versão vira só publicar a release.

## Cuidado com os prints

As capturas usam a base de demonstração. A tela de Clientes teve CPF, telefone,
e-mail e endereço substituídos por marcadores (`000.000.000-00`,
`cliente@exemplo.com`) antes de entrar aqui.

**Print novo que mostre dado pessoal passa pelo mesmo tratamento antes de subir.**

## O código-fonte do sistema não está aqui

Este repositório é só a página. O projeto em C# fica fora dele, de propósito.
