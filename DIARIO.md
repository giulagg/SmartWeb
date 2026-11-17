
DIÁRIO DE BORDO DO PROJETO SMARTWEB

INSTITUIÇÃO: SENAC 

Disciplina: Desenvolvimento Web 

Projeto: Resgate da SmartWeb

 Equipe: Equipe Prisma

Integrantes:
 Giulia Batista
 André Simões
 João Pedro Brasil
 Marriton Santos 


 Analise e reorganização inicial do código:

Data: 13/11/2026  

Categoria: Refatoração / Organização do código

Branch: `refactor/separar-arquivos`

Pull Request: #1

primeira situação: O projeto esta com toda a estrutura HTML, as regras CSS e o JavaScript juntos em um único arquivo, dificultando a identificação de cada parte do código

Procedimento realizado: Foram criadas as pastas `css` e `js`, com os arquivos `estilos.css` e `app.js`, respectivamente. As regras CSS e o bloco principal de JavaScript foram movidos  para esses arquivos, preservando o código original. As referências externas foram incluídas no HTML, renomeado para `index.html`.

Verificação: O projeto foi aberto pelo Live Server, e os arquivos externos foram identificados na aba Network do Chrome, sem erros HTTP. Os problemas originais de funcionamento e responsividade permanecem pendentes de correção.

Commits: Três commits específicos de reorganização, incluindo `8f484c8` — `refactor: extrair javascript para arquivo externo`.

Resultado: Estrutura inicial reorganizada, permitindo que as próximas intervenções em HTML, CSS e JavaScript sejam desenvolvidas e registradas separadamente.

Observação: Esta etapa não corresponde à resolução dos problemas identificados no diagnóstico inicial.

Responsável pelo registro:André Simões


Etapa 1 — Diagnóstico inicial

 Diagnóstico: auditoria de acessibilidade com Lighthouse

Data: 13/11/2026

Ferramenta:Google Chrome — Lighthouse

Página analisada: `index.html`, executada pelo Live Server.

Resultados obtidos:
Performance: 100
Acessibilidade: 44
Boas práticas: 92
SEO: 82

Problemas identificados: A auditoria apontou imagens sem atributo `alt` e combinações de cores de texto e fundo com contraste insuficiente e ausência de declaração do idioma principal da página (lang). Esses problemas dificultam o acesso às informações, especialmente para pessoas que utilizam leitores de tela ou apresentam dificuldades de percepção visual. 

Situação: Problemas identificados e ainda não corrigidos nesta etapa.

Meta: Alcançar pelo menos 90 pontos em acessibilidade, conforme exigência do roteiro.

Evidência: Captura de tela do Lighthouse realizada em 13/11/2026.

Responsável pelo registro: Giulia Batista

Problema 01 — Layout não responsivo

Data: 12/11/2026

Categoria:*CSS / Responsividade

Sintoma observado:
Ao testar o site em uma largura de 360 px, observa-se
que a página não se adapta adequadamente a tela.
O conteúdo aparece muito reduzido, dificultando
a leitura dos textos e a navegação.

O problema também foi observado em 768 px,
quando parte do conteúdo ultrapassou a área
visível do navegador.

Evidências:
- evidencias/antes/responsividade-360px-antes.png
- evidencias/antes/responsividade-768px-antes.png

Situação:*Problema identificado, ainda não corrigido.

Responsável pelo registro: André Simões

Problema 02 — Navegação por teclado

Data: 13/11/2026

Categoria: Acessibilidade

Sintoma observado:
Durante o teste utilizando apenas Tab, Shift+Tab, Enter 
e Espaço, não foi possível identificar visualmente o 
foco nos elementos da página. A navegação percebida 
ocorreu apenas na barra de ferramentas do navegador.

Evidências:*
Teste manual realizado utilizando 
apenas o teclado, conforme as orientações do roteiro.

Situação: Problema identificado, ainda não corrigido. 

**Responsável pelo registro:** Giulia Batista


Diagnóstico geral dos problemas do site

data:17/11/2026 

Ao analisar o arquivo `smartwebinformatica-desafio.html`, a equipe percebeu que os problemas se espalham por todas as camadas do projeto: o JavaScript quebra ao carregar a página, a estrutura HTML ignora a semântica e as regras de acessibilidade, e o CSS é rígido, não responsivo e com baixo contraste. Para organizar o trabalho, os problemas foram divididos por categoria (JavaScript, HTML, CSS e Acessibilidade, seguindo a classificação do roteiro) e distribuídos entre os integrantes por área de responsabilidade. Dentro do JavaScript, a minha parte ficou com os erros de sintaxe e variáveis, o carregamento do catálogo, a busca de produtos, os filtros por linha e a organização dos dados dos produtos. Cada problema foi registrado no Diário de Bordo com sintoma, causa, seção da apostila e commit próprio.

Problemas identificados, por categoria:

A) JavaScript (erros de sintaxe e variáveis, catálogo, busca, filtros e dados)

responsável: Marriton

1. O `window.onload = montaCatalogo()` executa a função imediatamente, antes de o HTML existir.
2. O laço do catálogo usa `i <= produtos.length`, passando uma posição além do fim da lista e gerando `TypeError`.
3. A propriedade `innerHtml` está escrita errada: o correto é `innerHTML`.
4. A condição `linhaAtual = "todas"` usa `=` (atribuição) em vez de comparação, então o filtro nunca funciona.
5. A função `filtra` usa `linhaAtual == l`, que só compara e nunca guarda a linha escolhida.
6. A busca usa `indexOf(termo) > 0`, ignorando resultados na posição 0 e diferenciando maiúsculas de minúsculas.
7. A busca procura apenas no nome, sobrescreve o catálogo com um único item e ignora o filtro de linha.
8. A variável `i` da busca é criada sem declaração (global implícita).
9. O texto digitado na busca entra via `innerHTML`, abrindo brecha de XSS.
10. Não há mensagem quando a busca não encontra nenhum produto.
11. O campo `preco` está como texto, então somas viram concatenação e os valores aparecem sem formatação em reais.
12. O catálogo não é agrupado por linha, e dados, regras e renderização estão misturados em funções grandes.
13. Os filtros são `<span>` com `onclick` no HTML, inacessíveis por teclado e sem indicar qual está ativo.

B) JavaScript (demais funcionalidades)

Responsável: joâo

14. `mostraAba` procura o id `"produto"`, mas o HTML usa `"produtos"`.
15. A função `adiciona` soma com `total` não inicializado (`NaN`) e usa `alert`.
16. A função `limpar` atribui `""` ao carrinho (que deveria ser um array) e não zera o contador.
17. A função `enviar` tem `getElemetById` escrito errado e usa `=` na comparação do e-mail.
18. A validação do formulário usa `alert` genérico, sem mostrar o erro junto do campo.
19. O botão do formulário dispara o envio e recarrega a página.
20. `copiar` usa `document.execCommand`, método obsoleto, que nem recebe o id.
21. O id `c-wa` está duplicado entre WhatsApp e telefone.
22. O FAQ abre por `onmouseover` e `nextSibling`, que não funciona por clique nem por teclado.

C) HTML 

responsável: a decidir

23. Faltam `<!DOCTYPE html>`, `lang`, `charset`, `viewport` e um `<title>` descritivo.
24. Há elementos obsoletos (`<font>`, `<center>`, `<marquee>`, `bgcolor`) e `<table>` usada para layout.
25. A hierarquia de títulos tem saltos e vários `<h1>`.
26. Imagens sem `alt` e campos de formulário sem `<label>`.
27. Faltam elementos semânticos (`header`, `nav`, `main`, `footer`) e `onclick` está espalhado pelo HTML.

D) CSS  

responsável: André

28. O layout é fixo (`width: 1100px`) e não é responsivo.
29. Há estilos inline e atributos visuais no HTML, fora da folha de estilos.
30. Uso excessivo de `!important` e regras duplicadas (`h1` definido duas vezes).
31. O CSS não usa Flexbox, Grid, variáveis nem unidades relativas.

E) Acessibilidade 

responsável: giulia

32. O contraste de cores é insuficiente (textos cinza claro sobre fundo branco).
33. O foco é removido (`outline: none !important`).
34. Elementos clicáveis são `div` e `span`, sem acesso por teclado.
35. Informações de estado das portas dependem só de cor (verde/vermelho).
36. Há animação piscante (`piscar`) e `marquee`, sem respeitar `prefers-reduced-motion`.
37. Mudanças dinâmicas (total, erros, cópia) não são anunciadas a leitores de tela (falta `aria-live`).




