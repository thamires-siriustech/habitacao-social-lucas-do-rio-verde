# Oferta habitacional de Lucas do Rio Verde (MT): entregas, demanda reprimida e o descompasso

Análise de dados sobre a política de habitação de interesse social em Lucas do Rio Verde, medindo quantas moradias a cidade efetivamente entregou, para quem, e como isso se compara à demanda da população — a partir de um dataset construído manualmente de fontes públicas.

> **Pergunta de negócio:** A oferta de habitação de interesse social em Lucas do Rio Verde acompanha a demanda da população que precisa dela?

---

## Este é o 2º projeto de uma análise em duas camadas

- **[Camada 1 — Projeção populacional e demanda habitacional](https://github.com/thamires-siriustech/previsao-populacional-lucas-do-rio-verde)** projetou a *demanda* futura por moradia a partir do crescimento populacional (1.100 a 1.800 novas unidades/ano até 2035).
- **Camada 2 (este repositório)** mede a *oferta* real: quantas moradias de interesse social a cidade entregou, e confronta com a demanda.

O cruzamento das duas camadas é o diferencial do projeto — uma análise que não existe publicamente para a cidade.

## Principais resultados

- **1.371 unidades de interesse social entregues** entre 2017 e 2026, de forma irregular (com um vazio de cinco anos entre 2017 e 2022).
- **Pipeline de 2.171 unidades em obra** — mais do que tudo já entregue, sinalizando uma mudança de patamar na política habitacional.
- **As entregas cobriram apenas ~24% da fila de espera de 2021** (5.800 famílias inscritas, 4.000 no perfil Faixa 1).
- A **demanda anual projetada** pela Camada 1 — mesmo no cenário mais conservador (1.098 moradias/ano) — **supera a oferta média histórica**. A conta estrutural só fecha se o pipeline se concretizar e o ritmo se mantiver.
- Política de **forte articulação federativa**: a maioria dos empreendimentos empilha recursos federais, estaduais e municipais.

## Metodologia

1. **Construção do dataset** — curadoria manual de fontes públicas (Prefeitura, MT Par/SiHab-MT, Ministério das Cidades, Caixa), já que não existe base estruturada de habitação municipal. Cada registro tem a URL da fonte.
2. **Análise de entregas** — unidades entregues por ano, com distinção rigorosa entre entregue, em obra e previsto (para não inflar números).
3. **Composição** — por tipo de moradia, faixa de renda e fonte de recurso.
4. **Cruzamento oferta × demanda** — confronto com a fila de espera e com a demanda anual projetada na Camada 1.

## Stack técnico

- **Python** — pandas, numpy
- **Visualização** — matplotlib
- **Ambiente** — Jupyter Notebook

## Como executar

```bash
git clone https://github.com/thamires-siriustech/habitacao-social-lucas-do-rio-verde.git
cd habitacao-social-lucas-do-rio-verde
pip install -r requirements.txt
jupyter notebook analise_habitacional_lucas_do_rio_verde.ipynb
```

Mantenha o notebook e os dois CSVs na mesma pasta. No Jupyter, use **Kernel → Restart & Run All**.

## Estrutura do repositório

```
habitacao-social-lucas-do-rio-verde/
├── analise_habitacional_lucas_do_rio_verde.ipynb   # análise completa
├── oferta_habitacional_lrv.csv                     # dataset de oferta (empreendimentos)
├── demanda_habitacional_lrv.csv                    # fila de espera (demanda reprimida)
├── requirements.txt
└── README.md
```

## Escopo e limitações

- **Escopo:** apenas habitação de interesse social (subsídio público). Alto padrão fica de fora; o único caso de renda mais alta (Parque Primavera) recebe flag para separação.
- **Dataset curado manualmente** — auditável (toda linha tem fonte), mas pode não capturar todos os empreendimentos.
- **Fila de espera é um ponto único (2021)** — série histórica exigiria pedido via LAI.
- **Investimento incompleto** — só o Vida Nova II tem valor consolidado; os demais exigiriam consulta a licitações.
- **Obra ≠ entrega** — o pipeline é uma promessa sujeita a atrasos.

## Fontes dos dados

Prefeitura de Lucas do Rio Verde, MT Par / SiHab-MT (Sistema de Habitação de Mato Grosso), Ministério das Cidades e Caixa Econômica Federal. URLs individuais na coluna `fonte_url` de cada dataset.

---

**Autora:** Thamires Martins da Silva
Projeto de portfólio em análise de dados — Camada 2 de 2.
