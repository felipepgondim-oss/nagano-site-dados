# nagano-site-dados

Rentabilidade, cota e PL de D-1 dos fundos exibidos no site da Nagano Investimentos. O site busca `cotas.json`
ao abrir, e por isso **a atualização diária não exige republicar o site** (não gasta créditos da Netlify).

- `historico/<fundo>.csv` (`data;cota;bench`): cota ajustada e benchmark. Até 30/set/2026 vieram das planilhas do
  SharePoint (`Site Nagano Historico Cotas`); daí em diante, o job `site_cotas` do `nagano-scheduler` emenda
  **um dia útil por vez** com o retorno diário OFICIAL da Bluedeck — do fundo e do benchmark ("IPCA + Yield IMAB"
  no TR, IBXX no FIA). Dia com posição em cálculo não entra: a emenda para e tenta de novo na próxima execução.
- `cotas.json`: cota e PL do último dia emendado + retornos dia/mês/ano/12M/24M/36M/início do fundo (`f`) e do
  benchmark (`b`), em %.
- Os fundos são identificados pelo **código do Bluedeck** (`bluedeck_id`), não pelo nome.
- **Não edite o histórico à mão** sem parar o job; para corrigir o passado, regrave o CSV inteiro.

| chave no site | bluedeck_id | CNPJ | fundo |
|---|---|---|---|
| `nagano-tr` | 5145 | 34.793.111/0001-14 | Nagano Total Return FIF – Classe de Investimentos em Ações – RL |
| `atlas-fia` | 58 | 13.083.227/0001-90 | Atlas One FIC FIA |

Formato: `data` em AAAA-MM-DD, `cota` (navps), `pl_mm` (PL em R$ milhões), `f`/`b` em %.
Todas as informações aqui são públicas (também saem no informe diário da CVM). Não coloque credenciais neste repositório.
