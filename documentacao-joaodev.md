# Documentação — João.DevCode

> Site portfólio e landing page de serviços de desenvolvimento web, sistemas e automações.
> **URL de produção:** hospedado na Vercel

---

## Estrutura de Arquivos

```
João Pedro - Desenvolvedor de Sistemas & Automações_files/
├── index.html          # Estrutura HTML da página
├── style.css           # Todos os estilos (design system + seções)
├── script.js           # Lógica JavaScript (navbar, animações, counters)
├── perfil.jpg          # Foto do desenvolvedor (seção Sobre)
├── siteadvocacia.png   # Imagem portfólio — Landing Page Advocacia
├── sitepsicologia.png  # Imagem portfólio — Landing Page Psicólogo
├── sistema-cnh.png     # Imagem portfólio — Sistema de Gestão CNH
├── sitebarbearia.png   # Imagem portfólio — Site Barbearia
├── siteagencia.png     # Imagem portfólio — Site Agência de Marketing
└── mentoriamedica.png  # Imagem portfólio — Landing Page Mentoria Médica
```

---

## Seções da Página ([index.html](file:///Users/joaopedro/Downloads/Jo%C3%A3o%20Pedro%20-%20Desenvolvedor%20de%20Sistemas%20&%20Automa%C3%A7%C3%B5es_files/index.html))

| Seção | ID | Descrição |
|---|---|---|
| Navbar | `#navbar` | Menu fixo com links e CTA WhatsApp |
| Hero | `#hero` | Chamada principal com badge, título, estatísticas |
| Sobre | `#sobre` | Foto + texto descritivo com lista de diferenciais |
| Serviços | `#servicos` | 3 cards de serviços oferecidos |
| Processo | `#como-trabalho` | 4 etapas do fluxo de trabalho |
| Portfólio | `#portfolio` | Grid com 6 projetos entregues |
| Depoimentos | `#depoimentos` | 3 cards de avaliações de clientes |
| CTA | `#cta` | Chamada final com botão WhatsApp |
| Footer | `#footer` | Logo, navegação e copyright |

---

## Design System ([style.css](file:///Users/joaopedro/Downloads/Jo%C3%A3o%20Pedro%20-%20Desenvolvedor%20de%20Sistemas%20&%20Automa%C3%A7%C3%B5es_files/style.css))

### Variáveis CSS (`:root`)

| Variável | Valor | Uso |
|---|---|---|
| `--bg` | `#080808` | Fundo principal (preto) |
| `--bg2` | `#111111` | Fundo seções alternadas |
| `--bg3` | `#161616` | Fundo de cards |
| `--red` | `#E63946` | Cor de destaque (vermelho) |
| `--red-dark` | `#c0303b` | Hover dos botões vermelhos |
| `--white` | `#ffffff` | Texto principal |
| `--gray` | `#888888` | Texto secundário |
| `--gray-light` | `#aaaaaa` | Texto levemente mais claro |
| `--border` | `rgba(255,255,255,0.08)` | Bordas sutis dos cards |
| `--transition` | `all 0.3s cubic-bezier(…)` | Transições padrão |
| `--radius` | `12px` | Borda arredondada padrão |
| `--container` | `1140px` | Largura máxima do conteúdo |

### Tipografia

| Fonte | Pesos | Aplicação |
|---|---|---|
| **Syne** | 700, 800 | Títulos (`h1`–`h4`), logo, números |
| **DM Sans** | 400, 500, 600, 700 | Corpo, parágrafos, botões, tags |

### Botões

| Classe | Estilo |
|---|---|
| `.btn` | Base — flex, padding, border-radius, font-weight 700 |
| `.btn-red` | Fundo vermelho, hover escurece e sobe 2px |
| `.btn-outline` | Transparente, borda branca semi-opaca |
| `.btn-lg` | Versão maior (padding 18px 40px, font 17px) |

### Animação `.fade-up`

Elementos com a classe `.fade-up` iniciam ocultos (`opacity: 0`, `translateY(40px)`) e ficam visíveis (`.visible`) quando entram na viewport via `IntersectionObserver`.

---

## JavaScript ([script.js](file:///Users/joaopedro/Downloads/Jo%C3%A3o%20Pedro%20-%20Desenvolvedor%20de%20Sistemas%20&%20Automa%C3%A7%C3%B5es_files/script.js))

### 1. Navbar — Active Link e Scroll

```js
// Detecta a seção visível e marca o link correspondente como .active
window.addEventListener('scroll', () => { ... });
```

- Percorre todas as `section[id]` e compara com o `scrollY`.
- Aplica a classe `.active` no `<a>` correspondente no navbar.

### 2. Menu Mobile

```js
navToggle.addEventListener('click', () => {
  navLinksContainer.classList.toggle('open');
});
```

- Botão hambúrguer (`.nav-toggle`) alterna a classe `.open` no menu.
- Links fecham o menu ao serem clicados.

### 3. Animações Scroll — `fade-up`

```js
const observer = new IntersectionObserver(callback, {
  threshold: 0.12,
  rootMargin: '0px 0px -40px 0px'
});
```

- Adiciona `.visible` quando o elemento entra na viewport.
- **Efeito escalonado** entre irmãos (delay de `120ms × índice`).
- Elementos do `#hero` ficam visíveis imediatamente no `load` (delay de 150ms por elemento).

### 4. Contador de Estatísticas

```js
function animateCounter(el) { ... }
```

Atributos HTML do elemento `.stat-number`:

| Atributo | Descrição | Exemplo |
|---|---|---|
| `data-target` | Valor final | `20` |
| `data-suffix` | Sufixo exibido | `+`, `★` |
| `data-decimal` | Casas decimais | `0` ou `1` |

- Animação de 1800ms com incremento a cada 30ms.
- Ativado via `IntersectionObserver` (threshold 0.5).

### 5. Smooth Scroll

```js
document.querySelectorAll('a[href^="#"]').forEach(anchor => { ... });
```

- Intercepta cliques em links âncora.
- Rola suavemente com offset de **80px** (compensar a navbar fixa).

---

## Responsividade

| Breakpoint | Mudanças |
|---|---|
| `≤ 1024px` | Grid de serviços vira 1 coluna |
| `≤ 768px` | Navbar mobile, grid portfólio/sobre/processo ajustados |
| `≤ 480px` | Hero, títulos e espaçamentos reduzidos |

---

## Contato / CTA

Todos os botões de contato apontam para:

```
https://api.whatsapp.com/send?phone=5531987147005
```

Para alterar o número, basta substituir `5531987147005` pelo novo número (formato DDI + DDD + número, sem espaços ou símbolos).

---

## Como Adicionar Projetos ao Portfólio

1. Adicione a imagem do projeto na pasta raiz (ex: `novoprojeto.png`).
2. Copie um bloco `.portfolio-card` existente em [index.html](file:///Users/joaopedro/Downloads/Jo%C3%A3o%20Pedro%20-%20Desenvolvedor%20de%20Sistemas%20&%20Automa%C3%A7%C3%B5es_files/index.html).
3. Atualize `src`, `alt`, `<h3>` e `<p>` com os dados do novo projeto.
4. Altere a tag (`Landing Page`, `Sistema Web`, `Site`, etc.) no `.tag` interno.

---

## Como Adicionar Depoimentos

1. Copie um bloco `.testimonial-card` em [index.html](file:///Users/joaopedro/Downloads/Jo%C3%A3o%20Pedro%20-%20Desenvolvedor%20de%20Sistemas%20&%20Automa%C3%A7%C3%B5es_files/index.html).
2. Atualize as estrelas, o texto, o nome, a profissão e a inicial do avatar.

---

## Dependências Externas (CDN)

| Recurso | URL |
|---|---|
| Google Fonts (Syne + DM Sans) | `fonts.googleapis.com` |
| Font Awesome 6.5.0 | `cdnjs.cloudflare.com` |

> Não há frameworks JS (React, Vue, etc.) — o site é **100% HTML/CSS/JS puro**.
