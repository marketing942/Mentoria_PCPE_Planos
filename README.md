# Mentoria PCPE

Página de venda direta da **Mentoria PCPE** (Polícia Civil de Pernambuco), com três planos
(Operacional, Supremo e Tático) indo direto para o checkout. É a mesma página da
[Mentoria PMPE](../pmpe) (`pmpe.cppem.com.br`), adaptada para a PCPE e já no modelo **edital
lançado**: alerta "Lançou o edital da PCPE", carimbo EDITAL LANÇADO e linha do edital.

Página estática: `index.html` + `styles.css` + `script.js` + `public/`, no sistema visual das landings
CPPEM (Oxanium + Rajdhani, ouro `#AF9256` sobre preto `#0A0A0B`).

## Dados da PCPE na página

Tirados das outras landings do CPPEM (`Venda Direta CPPEM/unificados` e `MentoriaPMPEePCPE`):

- **1.315 vagas**: 1.200 Agentes, 70 Escrivães e 45 Delegados.
- **Remuneração**: subsídio inicial de R$ 5.667,92 para Agente e Escrivão, chegando a R$ 13.537,00.

⚠️ Confira os dois contra o edital publicado: se o número de vagas ou o subsídio mudou, ajuste no
`index.html` (busque por `1.315` e por `Subsídio`).

## Datas do edital

Em `script.js`, preencha `CONFIG.edital` com o que o edital disser:

```js
edital: {
  publicacao: "12/10",
  inscricoes: "13/10 a 11/11",
  prova:      "14/12",
  taf:        "fev/2027",
  provaISO:   "2026-12-14T08:00:00-03:00"  // liga a contagem regressiva
}
```

Campo vazio mostra "Conforme edital". Sem `provaISO`, a contagem regressiva não aparece.

## Onde mexer

| O quê | Onde |
|---|---|
| Preços e links de checkout dos planos | `CONFIG.planos` no `script.js` |
| De/por do Supremo (hoje: total parcelado × à vista) | `CONFIG.planos.supremo` (`de`, `off`, `selo`) |
| Datas do edital | `CONFIG.edital` no `script.js` |

Os links de checkout são os mesmos do Plano de Combate do site (`pxa.cppem.com.br/lt/plano-de-combate-*`)
usados na página da PMPE. Se a PCPE tiver links próprios, troque no `CONFIG.planos`.

## A abertura

"MENTORIA" bate no vidro e "PCPE" sobe e colide. Toca uma vez por sessão. `?abertura=0` pula e
`?abertura=1` força.

## Medição (dataLayer)

`modelo_pagina` · `clique_checkout` (plano, valor), com `pagina: "mentoria-pcpe"`. Usa o mesmo
container de GTM das landings CPPEM.

## Pendências antes de publicar

- **Deploy**: criar um projeto na Vercel para esta pasta e definir o domínio (ex.: `pcpe.cppem.com.br`).
- **og:image** 1200×630 com URL absoluta, para o preview no WhatsApp e no Instagram.
- **Prova social**: a seção dos aprovados (fotos de alunos com o professor) foi tirada, porque ainda não
  há fotos suficientes de aprovados da Polícia Civil. Quando houver, ela pode voltar (está na página da
  PMPE).
