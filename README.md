# Landing Page — New Phisical

Página única (HTML + CSS + JS puro, sem dependências) para converter visita do Instagram em
conversa no WhatsApp e visita agendada na academia.

```
LP-New-Phisical/
├── index.html              ← a landing page inteira
├── assets/
│   ├── logo.png            ← logo branca, fundo removido (800px, 30 KB)
│   ├── logo-preta.png      ← versão preta, para fundos claros
│   ├── logo-original.png   ← arquivo original (2167px), guardado
│   ├── favicon.png         ← ícone da aba: o triângulo do atleta
│   └── fotos/              ← 13 fotos ILUSTRATIVAS do Unsplash (trocar pelas reais)
└── README.md
```

## Identidade

A marca é preto e branco puro, então o site é **dark** do começo ao fim, com duas seções claras
para dar respiro — e um **acento amarelo** (`#FFE500`, tirado do anel da foto de perfil) que carrega a energia
e marca os CTAs. Nas seções claras ele vira âmbar escuro (`#8A6A00`) para continuar legível.
Para trocar o acento, muda só `--neon` e `--neon-2` no `:root`; o site inteiro acompanha.

Tipografia: **Anton** (condensada, caixa alta) para os títulos, ecoando o peso da logo, e
**Inter** para leitura.

O slogan da bio — **"Outra academia. Outro nível."** — virou o `<h1>`, dividido em três linhas,
com a do meio vazada para criar contraste. Também roda no marquee logo abaixo do hero.

## Estrutura (ordem de persuasão)

| # | Bloco | Função na conversão |
|---|-------|---------------------|
| 1 | Hero + contadores | Slogan da marca + os 4 números que provam autoridade |
| 2 | Marquee neon | Reforça o slogan e as modalidades |
| 3 | Modalidades (3) | Cada card abre o WhatsApp com a mensagem daquela modalidade |
| 4 | Estrutura (seção clara) | Onde o "referência em estrutura" vira número |
| 5 | Planos 2026 (3) | Plano do meio destacado como "mais escolhido" (âncora de decisão) |
| 6 | Como começar (3 passos) | Tira o medo de quem nunca treinou |
| 7 | Instagram | Aproveita os 8,5 mil seguidores como prova social |
| 8 | Onde estamos + horários | Converte quem quer visitar |
| 9 | FAQ | Últimas objeções |
| 10 | CTA final + rodapé | Fechamento |
| + | WhatsApp flutuante e barra fixa no mobile | CTA sempre a um toque |

São **14 pontos de saída para o WhatsApp**, cada um com mensagem diferente já escrita — assim a
recepção sabe de onde a pessoa veio e você sabe qual bloco vende.

## ⚠️ O que precisa ser preenchido antes de publicar

1. **Valores dos planos** — os três cards estão com "Consultar". Coloque os preços reais de 2026,
   ou mantenha "Consultar" de propósito se a estratégia for forçar o contato (funciona, mas perde
   quem só quer comparar preço).
2. **Endereço da academia** — está como `Endereço da academia — Alfenas/MG`, e o link do Maps é
   uma busca pelo nome. Troque pelo link do Google Meu Negócio.
3. **Horários** — coloquei `Seg a sex 06h–22h · Sáb 08h–13h` como palpite de academia. **Confirme**,
   inclusive no JSON-LD lá no fim do arquivo.
4. **Modalidades** — usei musculação, pilates e aulas coletivas (os três que aparecem nos destaques
   do perfil). Se tiver mais (funcional, dança, avaliação física…), me fala que eu incluo.
5. **Fotos reais** — as 13 fotos em `assets/fotos/` são **ilustrativas, do Unsplash** (licença livre
   para uso comercial). Servem para o cliente visualizar o layout, mas **mostram outra academia**.
   Antes de publicar de verdade, troque pelas fotos da New Phisical — é a prioridade número um,
   porque o argumento central deles ("quase 100 equipamentos") só convence se for a estrutura real.
   Tamanhos: modalidades 900x620, estrutura 700x700, Instagram 600x600, og-cover 1200x630.
6. **O que entra em cada plano** — a lista de benefícios de cada card é suposição. Confirme com a
   recepção.
7. **Domínio** — troque `https://www.newphisical.com.br/` no canonical, nas tags `og:` e no JSON-LD.
8. **`assets/fotos/og-cover.jpg`** — já existe, mas é foto ilustrativa. Troque por uma foto real
   da academia com a logo aplicada.

## Configuração rápida

```js
const NEW = {
  telefone: '5535999171977',
  mensagemPadrao: 'Ola! Vim pelo site da New Phisical.'
};
```

## Rastreamento

`track()` já dispara para **GA4 (`gtag`)**, **Meta Pixel (`fbq`)** e **GTM (`dataLayer`)** — cole a
tag no `<head>` e os eventos (`cta_hero_visita`, `plano_trimestral`, `mod_pilates`, `cta_final`…)
começam a chegar. Marque todos como conversão.

## Como publicar

Site estático: Netlify, Vercel, Cloudflare Pages ou GitHub Pages. Depois é só trocar o link da bio
do Instagram (hoje vai direto pro `wa.me`) pela landing com UTM:

```
https://seudominio.com.br/?utm_source=instagram&utm_medium=bio&utm_campaign=perfil
```

## Já resolvido

- Arquivo único, sem framework nem biblioteca (só as fontes do Google)
- Responsivo de 320px ao desktop, com barra de CTA dedicada no mobile
- `prefers-reduced-motion` respeitado — todos os efeitos desligam sozinhos
- JSON-LD `ExerciseGym` com telefone, cidade e horários, para busca local
- Logo tratada: fundo preto removido, versão preta gerada e favicon recortado do símbolo
