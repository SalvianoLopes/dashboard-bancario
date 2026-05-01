# Plataforma de Gestão Operacional — Banco Digital

Painel de monitoramento de indicadores operacionais desenvolvido para instituição financeira do setor bancário. Permite acompanhamento em tempo real de 20 KPIs críticos com metas, alertas e evolução histórica.

![Dashboard](https://img.shields.io/badge/status-demo-f59e0b) ![Stack](https://img.shields.io/badge/stack-React%20%7C%20Chart.js%20%7C%20Supabase-1F4E79)

## Funcionalidades

- **Dashboard de KPIs** — visão consolidada com score de conformidade, indicadores em alerta e críticos
- **Análise por mês** — histórico de 13 meses com comparativo de evolução
- **Lançamento de dados** — formulário de entrada para atualização mensal dos indicadores
- **Gráficos interativos** — evolução temporal, distribuição por status e comparativo de metas
- **Drilldown** — detalhamento por indicador com gap em relação à meta
- **Export** — relatórios em PDF e Excel

## Stack

| Tecnologia | Uso |
|-----------|-----|
| React 18 | Interface (via CDN, sem build) |
| Chart.js 4 | Visualizações gráficas |
| Supabase | Banco de dados e API REST |
| DM Sans / DM Mono | Tipografia |

## Modo Demo

Este repositório contém uma versão de demonstração com **dados fictícios gerados localmente** — nenhuma conexão com banco de dados é necessária. As alterações feitas no formulário são aplicadas em memória durante a sessão.

Para conectar ao seu próprio banco de dados, edite as variáveis no `index.html`:

```js
var SUPABASE_URL = "https://seu-projeto.supabase.co";
var SUPABASE_ANON_KEY = "sua-chave-anon";
```

### Schema esperado

```sql
-- Tabela de configuração dos indicadores
CREATE TABLE config_indicadores (
  id SERIAL PRIMARY KEY,
  numero INT,
  nome TEXT,
  meta NUMERIC,
  direcao TEXT,   -- '≥' ou '≤'
  responsavel TEXT
);

-- Tabela de dados mensais
CREATE TABLE base_dados (
  id SERIAL PRIMARY KEY,
  mes TEXT,
  indicador TEXT,
  total_casos INT,
  dentro_prazo INT,
  resultado_pct NUMERIC,
  tombamento_compulsorio INT DEFAULT 0,
  updated_at TIMESTAMPTZ
);
```

## Como rodar

```bash
# Sem dependências — abrir direto no browser
open index.html

# Ou via servidor local
npx serve .
python -m http.server 8080
```

## Projeto

Desenvolvido sob medida para área de operações bancárias. Substituiu planilhas manuais de controle mensal por uma interface web interativa com histórico, alertas automáticos e exportação padronizada.

---

*Portfólio — [SalvianoLopes](https://github.com/SalvianoLopes)*
