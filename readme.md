<div align="center">

# 🗞️ Flyers Digitais

**Criar um produto digital MVP eficiente a partir do marketing tradicional.**

Panfletos, encartes e peças de e-mail marketing transformados em landing pages — com HTML, CSS e JavaScript puros.

</div>

---

## 🎯 Sobre o projeto

Todo negócio de varejo produz material impresso: encarte de oferta, panfleto de campanha, peça de e-mail marketing fatiada em faixas. Esse material morre em dias. Este projeto pega essas peças e as transforma em **landing pages** — páginas que se compartilham por WhatsApp, abrem no celular, têm botão de ação e vivem além da campanha.

O repositório tem duas camadas:

- **O catálogo** (`index.html` na raiz) — a vitrine de todas as campanhas já digitalizadas, uma pilha de encartes que cresce a cada projeto novo
- **Os projetos** (`projeto-1/`, `projeto-2/`…) — cada campanha em sua própria pasta, com página, assets e o PDF original

## 🎓 Finalidade pedagógica

Este é um projeto de **ensino**, desenvolvido para aulas de desenvolvimento front-end. A marca **ABC da Construção** — a maior especialista em acabamentos do Brasil, fundada em Juiz de Fora — é usada como **estudo de caso**: uma empresa real, com identidade visual, produtos e canais reais, dá peso de mercado ao exercício.

Por isso, as páginas são **mockups**: formulários não enviam dados, carrinho e busca não funcionam, preços e links de produto são ilustrativos. Todo elemento fictício está marcado com `*` e explicado no rodapé de cada página. Nenhum dado é coletado.

O que o aluno pratica aqui não é só HTML/CSS/JS — é o raciocínio de produto: **ler uma peça impressa, entender sua intenção de venda, e reconstruí-la como experiência digital moderna.**

## 📁 Estrutura

```text
flyers-digitais/
├── index.html              # catálogo de campanhas
├── readme.md
├── projeto-1/              # Aniversário 69 anos
│   ├── index.html
│   └── assets/
│       ├── abc-da-construcao-emailmkt.jpg      # imagem principal do encarte
│       ├── abc-da-construcao-emailmkt-2.jpg    # faixas do e-mail marketing
│       ├── ... -6.jpg
│       └── pdf-emailmkt.pdf                    # peça original
└── projeto-2/              # Especial 9.9
    ├── index.html
    └── assets/                                 # mesma estrutura
```

## 🗂️ O catálogo

Página única que lista todas as campanhas, da mais recente à mais antiga. Cada entrada mostra o encarte real em tamanho grande, o nome da campanha, o período, uma frase de contexto, um botão para abrir a página e um link para o PDF original.

**Dado dirigido por JavaScript:** as campanhas ficam num array `campanhas[]` dentro do próprio `index.html`. Adicionar uma campanha nova é acrescentar um objeto e criar a pasta correspondente — o catálogo se reconstrói sozinho.

```js
{
  pasta: 'projeto-3',
  nome: 'Nome da campanha',
  complemento: 'Frase curta de apoio',
  periodo: 'Quando aconteceu',          // opcional — se vazio, a linha não aparece
  descricao: 'O que a campanha vendia.',
  ordem: 3                               // maior aparece primeiro
}
```

## 🏗️ Os projetos

Cada projeto é um **arquétipo diferente** de página promocional — os dois que o aluno mais vai encontrar no mercado.

### Projeto 1 — Aniversário 69 anos · *Storefront promocional*

A promoção **dentro da loja completa**. Réplica fiel do storefront da ABC (header com busca, conta e carrinho; menu de categorias rolável; departamentos), com a campanha de aniversário encaixada nele.

| Seção | O que ensina |
|---|---|
| Aviso + header sticky | `position: sticky`, layout flex, header de e-commerce |
| Menu de categorias | Rolagem horizontal com `overflow-x`, scrollbar oculta |
| Hero | Grid de duas colunas, tipografia fluida com `clamp()` |
| Departamentos | Lista de texto como mega-menu — sem emoji, sem ícone decorativo |
| Vitrine (4 produtos) | Cards de produto: `aspect-ratio`, tags posicionadas, preço de/por |
| Produto em destaque (×2) | Seções alternadas com `order` no grid |
| Lojas (11 estados) | Grid responsivo em 3 estágios (2 → 3 → 4 colunas) |
| Rodapé institucional | Grid de 4 colunas, `<time>` |
| **Modal de cupom** | `<dialog>` nativo, `showModal()`, `::backdrop`, validação HTML5, feedback inline, `setTimeout`, tecla Esc |

**JavaScript:** modal com estado (aberto/dispensado), timing de 4 s, formulário com `reportValidity()` e confirmação inline — sem `alert()`.

**Nível sugerido:** intermediário/avançado.

### Projeto 2 — Especial 9.9 · *Landing page de campanha*

O encarte **vira a própria página**. Uma promoção, uma conversão. As imagens do e-mail marketing já são faixas horizontais — o layout respeita a proporção original em vez de cortá-las em cards.

| Seção | O que ensina |
|---|---|
| Hero | Título num peso só, imagem edge-to-edge no mobile |
| Marcas | Lista inline simples |
| Vitrine em faixas | Grid que preserva a proporção da imagem, sem `object-fit` |
| Dúvidas | `<details>`/`<summary>` — acordeão acessível **sem JavaScript obrigatório** |
| Contato | Links `tel:`, `mailto:` e `wa.me` |
| Rodapé | Disclaimer de mockup |

**JavaScript:** 6 linhas — ao abrir uma pergunta, fecha as outras. Refinamento de UX sobre um componente que já funciona nativamente.

**Nível sugerido:** básico/intermediário. É o projeto pra começar.

## 🎨 Sistema visual compartilhado

Um sistema só para catálogo e projetos — o aluno vê **reuso de tokens** entre três páginas diferentes.

| Token | Valor | Uso |
|---|---|---|
| `--papel` | `#ffffff` | Folha do encarte |
| `--parede` | `#ececea` / `#f3f3f1` | Fundo, cimento |
| `--tinta` | `#262626` | Texto |
| `--cinza` | `#6b6b66` | Texto secundário |
| `--vermelho` | `#dc2626` | **Único acento** — botão, preço, wordmark |
| `--amarelo` | `#facc15` | **Só** a tag de desconto |

- **Tipografia:** [Archivo](https://fonts.google.com/specimen/Archivo), uma família — 900 expandido nos títulos (voz de cartaz de oferta), 700 em preço e botão, 400 no corpo
- **Forma:** raio zero, borda de 1 px, sem sombra difusa — o encarte é papel
- **Movimento:** nenhuma animação de entrada; só em resposta a ação do usuário
- **Layout:** mobile-first, breakpoint em 48 rem, largura máxima 72 rem

### O que este projeto evita de propósito

Fundo escuro com gradiente, cards idênticos arredondados com sombra, uma palavra colorida no título, rótulos em caixa alta espaçada, setas `→` em botões, emoji como ícone, animação de entrada em cada seção. São os padrões que fazem uma página parecer template — e o exercício é fazer o contrário.

## ✅ Convenções técnicas

- HTML semântico: `header`, `main`, `section`, `footer`, um `h1` por página
- `alt` descritivo em toda imagem; `:focus-visible` visível; `prefers-reduced-motion` respeitado
- `<meta name="description">` e Open Graph em toda página (preview no WhatsApp)
- `rel="noopener noreferrer"` em links externos; `loading="lazy"` abaixo da dobra
- CSS puro, variáveis em `:root`, comentários curtos explicando o **porquê** de decisões não óbvias
- Sem framework, sem build, sem dependência além da fonte

## ⚙️ Como rodar

Projeto estático. Abra a pasta num servidor local — [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) no VS Code, ou:

```bash
npx serve .
```

Abrir direto pelo sistema de arquivos (`file://`) funciona para as páginas dos projetos; o catálogo também, porque os dados estão inline.

## ➕ Adicionando uma campanha

1. Crie `projeto-N/` com `index.html` e `assets/` (imagem principal, faixas, PDF original)
2. Acrescente o objeto em `campanhas[]` no `index.html` da raiz
3. Marque todo elemento fictício com `*` e mantenha o disclaimer no rodapé

## 📚 Referência

[ABC da Construção](https://www.abcdaconstrucao.com.br) — marca usada como estudo de caso. Este repositório não tem vínculo comercial com a empresa; as páginas são exercícios didáticos e não representam ofertas vigentes.

---

Feito com ❤️ por [Douglas A. B. Novato](https://www.linkedin.com/in/douglasabnovato/) 👋🏽