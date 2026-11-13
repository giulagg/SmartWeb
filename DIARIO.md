
# DIÁRIO DE BORDO — SMARTWEB

## Identificação

**Disciplina:** Desenvolvimento Web I

**Projeto:** Resgate da SmartWeb

**Equipe:** Equipe Prisma

**Integrantes:**
- Giulia Batista
- Marriton Santos
- André Simões
- João Pedro Brasil 


## Reorganização inicial do código — Separação dos arquivos

**Data:** 13/11/2026  

**Categoria:** Refatoração / Organização do código

**Branch utilizada:** `refactor/separar-arquivos`

**Pull Request:** #1

**Situação inicial:** O projeto apresentava a estrutura HTML, as regras CSS e o JavaScript principal juntos em um único arquivo, dificultando a identificação e a manutenção de cada parte do código separadamente.

**Procedimento realizado:** Foram criadas as pastas `css` e `js`, com os arquivos `estilos.css` e `app.js`, respectivamente. As regras CSS e o bloco principal de JavaScript foram transferidos para esses arquivos, preservando o código original. As referências externas foram incluídas no HTML, posteriormente renomeado para `index.html`.

**Verificação:** O projeto foi aberto pelo Live Server, e os arquivos externos foram identificados na aba Network do Chrome, sem erros HTTP de carregamento. Os problemas originais de funcionamento e responsividade permaneceram pendentes de correção.

**Commits:** Três commits específicos de reorganização, incluindo `8f484c8` — `refactor: extrair javascript para arquivo externo`.

**Resultado:** Estrutura inicial reorganizada, permitindo que as próximas intervenções em HTML, CSS e JavaScript sejam desenvolvidas e registradas separadamente.

**Observação:** Esta etapa não corresponde à resolução dos problemas identificados no diagnóstico inicial.

**Responsável pelo registro:** André Simões


## Etapa 1 — Diagnóstico inicial


### Problema 01 — Layout não responsivo

**Data:** 12/11/2026

**Categoria:** CSS / Responsividade

**Sintoma observado:**
Ao testar o site em uma largura de 360 px, observa-se
que a página não se adapta adequadamente a tela.
O conteúdo aparece muito reduzido, dificultando
a leitura dos textos e a navegação.

O problema também foi observado em 768 px,
quando parte do conteúdo ultrapassou a área
visível do navegador.

**Evidências:**
- evidencias/antes/responsividade-360px-antes.png
- evidencias/antes/responsividade-768px-antes.png

**Situação:** Problema identificado, ainda não corrigido.

**Responsável pelo registro:** André Simões


### Problemas identificados

| Nº | Data | Categoria | Sintoma observado |
|---|---|---|---|
| 01 | | | |
| 02 | | | |
| 03 | | | |

### Reflexão sobre a experiência de uso

[Escrever um parágrafo comparando as dificuldades
de um usuário comum, de uma pessoa que utiliza
leitor de tela, de alguém que usa zoom e de quem
acessa o site pelo celular.]

## Etapas 2 a 8 — Correções realizadas

| Nº | Data | Sintoma observado | Causa encontrada | Seção da apostila | O que foi feito | Commit | Responsável |
|---|---|---|---|---|---|---|---|
| 01 | | | | | | | |
| 02 | | | | | | | |

## Problemas ainda não resolvidos

[Registrar problemas pendentes e o que a equipe
tentou fazer para resolvê-los.]
