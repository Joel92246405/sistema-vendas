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
   git tag v1.0.4 && git push origin v1.0.4
   ```

   A página aponta hoje para `SistemaVendas_Setup_1.0.3.0.exe`.

   **A partir da 1.0.3 existe um instalador só.** Não há mais versão "Trial"
   separada: quem instala começa em avaliação e vira licenciado ativando dentro
   do sistema. O mesmo arquivo serve ao download da página e à entrega da venda.

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
`cliente@exemplo.com`) antes de entrar aqui. No **Extrato do Cliente**, o
telefone do rodapé foi mascarado para `(16) 99999-0000` — trocado no rótulo
antes de desenhar a tela, e não editando o pixel depois, para o texto sair com
a mesma fonte do resto da imagem.

**Print novo que mostre dado pessoal passa pelo mesmo tratamento antes de subir.**

## Pedir o e-mail antes do download

O diálogo que abre ao clicar em Baixar tem duas etapas: o e-mail e o aviso do
SmartScreen. **A primeira vem desligada** — enquanto as constantes no fim do
`index.html` estiverem vazias, o download acontece direto, como sempre.

Para ligar, crie um formulário do Google com dois campos (e-mail e uma caixa de
aceite) e pegue três valores:

1. No formulário: menu de três pontos → **Obter link pré-preenchido**
2. Preencha qualquer coisa e clique em **Obter link**
3. O link copiado é assim:

   ```
   https://docs.google.com/forms/d/e/SEU_ID/viewform?usp=pp_url&entry.111111=x&entry.222222=y
   ```

   - troque `/viewform?...` por `/formResponse` → é o `ENDERECO`
   - `entry.111111` é o `CAMPO_EMAIL`
   - `entry.222222` é o `CAMPO_ACEITE`

Cole os três no bloco do `<script>`, no fim do `index.html`.

**Por que formulário do Google e não Firebase:** os dois guardam o dado na
Google de qualquer jeito, então a independência que o Firebase daria é menor do
que parece. O que muda é o risco. Uma regra de segurança errada no Firestore
deixa **a lista inteira de e-mails aberta para qualquer um baixar**, em silêncio.
Aqui o pior caso é perder um e-mail.

**Se o envio falhar, o download libera assim mesmo.** Bloqueador de anúncio
derruba essa requisição com frequência, e prender o cliente por causa de um
formulário quebrado custa mais que a lista.

## Contato: só e-mail

O WhatsApp saiu da página, do sistema e do instalador em 30/07/2026. Canal
aberto com número pessoal dentro de binário distribuído não se desfaz depois.
Se um dia voltar, que seja um número separado.

## O código-fonte do sistema não está aqui

Este repositório é só a página. O projeto em C# fica fora dele, de propósito.
