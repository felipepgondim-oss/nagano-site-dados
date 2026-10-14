# nagano-site-dados

Cota e PL de D-1 dos fundos exibidos no site da Nagano Investimentos. O site busca este arquivo ao abrir, e por isso
**a atualização diária não exige republicar o site** (não gasta créditos da Netlify).

- `cotas.json` é gravado todo dia útil por um job do `nagano-scheduler`, depois que a posição é **liberada** no Bluedeck.
- Os fundos são identificados pelo **código do Bluedeck** (`bluedeck_id`), não pelo nome; o CNPJ serve de conferência.

| chave no site | bluedeck_id | CNPJ | fundo |
|---|---|---|---|
| `nagano-tr` | 5145 | 34.793.111/0001-14 | Nagano Total Return FIF – Classe de Investimentos em Ações – RL |
| `atlas-fia` | 58 | 13.083.227/0001-90 | Atlas One FIC FIA |

Formato: `data` em AAAA-MM-DD, `cota` (navps) e `pl_mm` (PL em R$ milhões).
Todas as informações aqui são públicas (também saem no informe diário da CVM). Não coloque credenciais neste repositório.
