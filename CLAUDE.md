# CLAUDE.md

Guia para trabalhar neste repositório com Claude Code.

## Visão Geral

Site portfólio / landing page de **João.DevCode** — desenvolvedor de sistemas, landing pages e automações. Stack **100% HTML/CSS/JS puro**, sem frameworks, sem build step. Hospedado na Vercel.

Documentação completa das seções, design system e componentes em [documentacao-joaodev.md](documentacao-joaodev.md).

## Estrutura

```
index.html          # Página única com todas as seções
style.css           # Design system + estilos (variáveis CSS em :root)
script.js           # Navbar scroll, fade-up observer, counters, smooth scroll
perfil.jpg          # Foto da seção Sobre
*.png               # Imagens do portfólio (siteadvocacia, sistema-cnh, etc.)
```

## Como rodar

Não há build. Abrir [index.html](index.html) direto no navegador, ou servir a pasta:

```bash
python3 -m http.server 8000
```

## Design System

Tokens em `:root` de [style.css](style.css):

- **Cores**: `--bg` `#080808` (fundo), `--red` `#E63946` (destaque), `--white`, `--gray`
- **Tipografia**: `Syne` (títulos, pesos 700/800) + `DM Sans` (corpo, 400–700)
- **Botões**: `.btn` + `.btn-red` / `.btn-outline` / `.btn-lg`
- **Animação scroll**: adicionar `.fade-up` em um elemento — o `IntersectionObserver` em [script.js](script.js) aplica `.visible` quando entra na viewport, com efeito escalonado entre irmãos

## Convenções ao editar

- **Não introduzir frameworks ou bundlers** — manter HTML/CSS/JS puro
- **Links de contato**: todos apontam para `https://api.whatsapp.com/send?phone=5531987147005`. Trocar em um único lugar exige `replace_all`
- **Novos projetos no portfólio**: duplicar um bloco `.portfolio-card` em [index.html](index.html) e adicionar a imagem na raiz
- **Novos depoimentos**: duplicar `.testimonial-card` (estrelas, texto, avatar com inicial)
- **Contadores**: elementos `.stat-number` usam `data-target`, `data-suffix`, `data-decimal` — a animação é disparada via `IntersectionObserver` em [script.js:76](script.js)
- **Smooth scroll**: offset fixo de `80px` para compensar a navbar (ver [script.js:102](script.js))

## Responsividade

Breakpoints em [style.css](style.css):
- `≤ 1024px`: serviços/portfólio/depoimentos viram 1 coluna
- `≤ 768px`: navbar mobile com `.nav-toggle` + menu `.open`
- `≤ 480px`: hero e títulos reduzidos

## Dependências externas (CDN)

- Google Fonts: Syne + DM Sans
- Font Awesome 6.5.0
