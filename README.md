# Redes Ceará · Diagnóstico Territorial

Diagnóstico que mapeia pobreza, inclusão produtiva, segurança alimentar e rede institucional nos municípios onde a Redes Ceará atua na Região Metropolitana de Fortaleza: **Fortaleza e Maracanaú** — 57 bairros, cerca de 585 mil habitantes acompanhados.

A entrega é composta por páginas HTML estáticas, apresentações de slides (HTML + PDF) e as bases de dados, pensadas para leitura direta pelo cliente, sem backend ou build.

> **Comece por `LEIA-ME.html`** (guia do pacote) ou abra direto o `index.html`.

## Conteúdo da entrega

| Arquivo | O que é | Offline |
|---|---|:--:|
| `LEIA-ME.html` | Guia de uso do pacote (comece por aqui). | ✓ |
| `index.html` | Página inicial com seleção de município e contexto do diagnóstico. | ✓ |
| `fortaleza.html` | Painel interativo de Fortaleza: 13 bairros em 2 territórios (Grande Bom Jardim e Grande Mucuripe), 8 abas. | precisa de internet |
| `maracanau.html` | Painel interativo de Maracanaú: 44 bairros em 6 regiões, 8 abas. | precisa de internet |
| `resumo_executivo.html` | Hub das três apresentações de slides. | ✓ |
| `report_fortaleza.html` / `.pdf` | Apresentação executiva de Fortaleza (19 slides). | ✓ |
| `report_maracanau.html` / `.pdf` | Apresentação executiva de Maracanaú (19 slides). | ✓ |
| `report_geral.html` / `.pdf` | Síntese do trabalho (15 slides). | ✓ |
| `policy_brief.html` | Policy brief com a revisão de literatura e as recomendações. | ✓ |
| `assets/images/` | Imagens e logos usados nas páginas. | ✓ |
| `data/` | Bases brutas e dicionário de dados. | ✓ |

Cada painel municipal traz 8 abas: Visão Geral, Demografia, Vulnerabilidade, Infraestrutura, Economia, Sociedade Civil, Síntese e Adicionalidade.

## Como abrir

Por serem páginas HTML estáticas, basta abrir `index.html` no navegador — nenhuma instalação é necessária.

**Importante (offline x online):** quase tudo funciona offline. As exceções são os **dois painéis interativos** (`fortaleza.html` e `maracanau.html`): os mapas (Leaflet + CARTO) e os gráficos (Chart.js) carregam de servidores externos, então **precisam de conexão à internet**. Sem internet, use a versão online ou os PDFs/apresentações.

Versão online (interativa): **https://bfernlucas.github.io/redes_ceara/**

Para rodar com um servidor local (evita travas de CORS em alguns navegadores):

```bash
python3 -m http.server 8000
# abrir http://localhost:8000
```

## Estrutura

```
redes_ceara/
├── LEIA-ME.html            # guia do pacote (comece por aqui)
├── README.md
├── index.html              # landing
├── fortaleza.html          # painel Fortaleza
├── maracanau.html          # painel Maracanaú
├── resumo_executivo.html   # hub das apresentações
├── report_fortaleza.html   # deck Fortaleza  (+ .pdf)
├── report_maracanau.html   # deck Maracanaú  (+ .pdf)
├── report_geral.html       # deck Síntese    (+ .pdf)
├── policy_brief.html       # policy brief
├── assets/
│   └── images/             # imagens e logos
└── data/                   # bases brutas e dicionário
    ├── Agregados_por_bairros_renda_responsavel_BR.csv
    ├── cnpj_empresas_fortaleza_maracanau_aliment.csv
    ├── cnpj_fortaleza_bairros_estudo.xlsx
    ├── estabelecimentos_com_porte_maracanau.xlsx
    └── dicionario_de_dados_renda_responsavel.xlsx
```

A pasta `data/` guarda as bases utilizadas na construção dos indicadores. Os painéis HTML já trazem os dados embutidos, então não dependem desses arquivos em tempo de execução; ficam versionados para rastreabilidade.

## Fontes de dados

- **IBGE** — Censo 2022, setores censitários e agregados por bairro
- **MDS / CadÚnico** — 2025
- **IPEA** — Mapa das OSCs, 2024
- **Receita Federal** — CNPJs por bairro, 2024
- **INEP** — Censo Escolar, 2023
- **CNES / DataSUS** — 2024
- **SSPDS-CE** — indicadores de segurança, 2024
- **Cartografia** — OpenStreetMap / CARTO

## Metodologia resumida

Os painéis cruzam indicadores de vulnerabilidade (extrema pobreza, CadÚnico, renda), infraestrutura (esgoto, CRAS, unidades de saúde), economia local (MEIs, MPEs, médias e grandes empresas) e sociedade civil organizada (OSCs) em dois recortes territoriais:

- **Fortaleza**: agregação dos 13 bairros de atuação da Redes Ceará em 2 territórios (Grande Bom Jardim e Grande Mucuripe).
- **Maracanaú**: todos os 44 bairros do município, agrupados nas 6 regiões político-administrativas.

A aba **Adicionalidade** aplica sobre esses indicadores uma leitura qualitativa em três pilares (necessidade relativa, viabilidade institucional e vácuo de articulação), cruzando com o perfil dos parceiros da Redes Ceará para sugerir alocação preferencial.

## Tecnologia

HTML, CSS e JavaScript puros. Sem framework, sem build. Dependências externas, carregadas via CDN (por isso os painéis interativos pedem internet):

- **Leaflet + Leaflet.markercluster + CARTO basemaps** — mapas
- **Chart.js** e **D3** — gráficos
- **Google Fonts (Inter)** — tipografia (degrada para fonte do sistema se offline)

## Realização e Parceria

- **Realização:** Instituto Localiza · Movimento Bem Maior · Somos Um
- **Parceria:** Fundação Dom Cabral · Pacto Contra a Fome

---

Elaborado por Lucas Fernandes · 2026 · limbersocial@gmail.com
