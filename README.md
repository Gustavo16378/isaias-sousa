# Isaias de Sousa | Corretor de Imóveis

Site one page do corretor Isaias de Sousa, que atua em Palmas (TO) pela Imobiliária Ricanato. Apresenta o corretor, suas especialidades e uma vitrine de imóveis, com contato direto pelo WhatsApp.

## Stack

| Peça | Escolha |
|---|---|
| Framework | React 19 + TypeScript |
| Build | Vite 6 |
| Estilo | Tailwind CSS 3 (paleta preto, prata e dourado) |
| Animações | Framer Motion |
| Ícones | Lucide React |
| Sanitização | DOMPurify |
| Tipografia | Playfair Display + Inter (Google Fonts) |

## Seções

1. **Hero**, com fundo em parallax e chamada para contato
2. **Sobre**, com fotos e trajetória do corretor
3. **Serviços**, as especialidades (residencial, alto padrão, lançamentos)
4. **Imóveis**, vitrine com filtro por tipo e modal de detalhes
5. **Processo**, as etapas do atendimento
6. **Contato**, formulário que gera a mensagem no WhatsApp
7. **Rodapé**

## Detalhes de implementação

- **SEO sem biblioteca.** As tags `title`, `meta`, Open Graph, Twitter Card e o JSON-LD `RealEstateAgent` são renderizadas direto no JSX, usando o suporte nativo a metadata do React 19.
- **Formulário sem backend.** O contato monta uma mensagem formatada e abre o `wa.me` do corretor. Antes disso, aplica honeypot (campo oculto `website`), limite de um envio a cada 5 segundos e sanitização de nome e mensagem com DOMPurify.
- **Navbar com scroll spy.** Um `IntersectionObserver` marca a seção ativa no menu, e o hook `useScrollDirection` detecta a direção da rolagem com um limiar para evitar oscilação.
- **Conteúdo centralizado em dados.** Informações do corretor e SEO ficam em `src/data/site.ts` e os imóveis em `src/data/imoveis.ts`, tipados em `src/types`. WhatsApp, e-mail e Instagram podem ser sobrescritos por variáveis `VITE_*`.
- **Modal acessível por teclado.** O modal de imóvel fecha com `Esc`, trava a rolagem do `body` enquanto aberto e alterna as fotos com `AnimatePresence`.

## Como rodar

```bash
npm install        # instala as dependências (.npmrc usa legacy-peer-deps)
cp .env.example .env  # opcional: define WhatsApp, e-mail e Instagram
npm run dev        # servidor de desenvolvimento
npm run build      # checagem de tipos + build de produção em dist/
npm run preview    # serve o build localmente
```

## Estrutura

```
src/
├── sections/     # seções da página (Navbar, Hero, Sobre, ... , Footer)
├── components/   # card e modal de imóvel, barra de progresso
│   └── ui/       # Badge, Button, SectionLabel
├── data/         # site.ts (corretor e SEO) e imoveis.ts (vitrine)
├── hooks/        # useScrollDirection
├── types/        # tipos de Imovel, filtros e formulário
└── public/photos # fotos do corretor, importadas pelos componentes
```

## Autor

Desenvolvido por [Gustavo Barbosa Lima](https://gustavodev.dev).
