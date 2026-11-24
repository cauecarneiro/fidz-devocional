# Fidz Devocional

Site de devocional diário da marca @usefidz, pensado para ser aberto por NFC numa pulseira: salmo, frase, reflexão e prática do dia, com um modelo de imagem para postar nos stories do Instagram.

Site · Web (Next.js) · 2026

[Site no ar](https://fidz-devocional-three.vercel.app)

## O que faz

- Mostra a cada dia um salmo, uma frase, uma reflexão e uma prática.
- Escolhe o conteúdo do dia sem repetir ao longo do ano: cada item só volta depois que todos os outros já apareceram.
- Segue o Calendário Fidz, com 12 temas mensais (por exemplo, "Recomeço & Propósito" em janeiro e "Perseverança" em março) que filtram os salmos do mês.
- Tem a tela `/share`, que monta um modelo de story com o conteúdo do dia, para copiar a imagem (com fundo transparente) e colar no Instagram.
- Funciona sem conta: o aparelho recebe um identificador aleatório, guardado no `localStorage`.

## Meu papel

Desenvolvimento do site, sozinho: os nove commits do repositório são de Cauê Carneiro (de 11/03/2026 a 14/07/2026), incluindo as correções do botão de copiar e dos botões da tela de compartilhar no Safari do iOS.

## Como foi feito

- **Next.js 16 com App Router e TypeScript:** a página inicial está em `app/page.tsx` e a tela de compartilhar em `app/share/page.tsx`.
- **Conteúdo em arquivos locais:** `lib/salmosData.ts`, `lib/frasesData.ts`, `lib/reflexoesData.ts` e `lib/praticasData.ts`; não há banco de dados nem servidor próprio.
- **Sem repetição no ano:** `lib/dailyContent.ts` embaralha cada lista de forma determinística (Fisher-Yates com semente por usuário e ano) e usa o dia do ano como índice. O salmo usa a lista filtrada pelo tema do mês, em `lib/calendarioFidz.ts`.
- **Imagem do story no navegador:** `html2canvas` gera a imagem, e a cópia usa a API de área de transferência com ajustes para o Safari do iOS.
- **Estilo com Tailwind CSS 4** e fontes por `next/font`.

## Tecnologias

Next.js 16, React 19, TypeScript, Tailwind CSS 4, html2canvas, ESLint.

## Como rodar

Requisitos: Node.js e npm.

```bash
npm install
npm run dev
```

Abra [http://localhost:3000](http://localhost:3000). Outros comandos: `npm run build`, `npm start` e `npm run lint`.

---
Feito por Cauê Crillanovick · [portfólio](https://cauecarneiro.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/cau%C3%AA-carneiro)
