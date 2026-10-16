# Oferta habitacional de Lucas do Rio Verde (MT): entregas, demanda reprimida e o descompasso

Análise de dados sobre a política de habitação de interesse social em Lucas do Rio Verde, medindo quantas moradias a cidade efetivamente entregou, para quem, e como isso se compara à demanda da população — a partir de um dataset construído manualmente de fontes públicas.

> **Pergunta de negócio:** A oferta de habitação de interesse social em Lucas do Rio Verde acompanha a demanda da população que precisa dela?

---

## Este é o 2º projeto de uma análise em duas camadas

- **[Camada 1 — Projeção populacional e demanda habitacional](https://github.com/thamires-siriustech/previsao-populacional-lucas-do-rio-verde)** estima a *demanda bruta total* por moradia a partir do crescimento populacional (aproximadamente 1.121 a 1.816 novas unidades/ano entre 2027 e 2035, conforme o cenário).
- **Camada 2 (este repositório)** mede a *oferta* real: quantas moradias de interesse social a cidade entregou, e confronta com a demanda.

O cruzamento das duas camadas é o diferencial do projeto — uma análise que não existe publicamente para a cidade.

## Principais resultados

- Entre 2017 e 2026, a base registra **1.084 casas/apartamentos entregues** e **287 lotes urbanizados**. O total de 1.371 reúne categorias diferentes e não equivale a 1.371 casas prontas.
- O pipeline inclui **2.000 casas em construção** dentro do escopo social estrito. Outras 171 unidades em obra pertencem a um empreendimento marcado fora desse escopo e ficam separadas do indicador principal.
- A fila de espera divulgada em 2021 registrava **5.800 famílias**, das quais 4.000 no perfil Faixa 1. Como não há ligação individual entre entregas e famílias atendidas, o projeto não estima percentual de cobertura nem déficit residual pela simples subtração de totais.
- A Camada 1 projeta demanda habitacional bruta total de aproximadamente **1.121 a 1.816 moradias por ano** entre 2027 e 2035. A oferta social histórica de casas/apartamentos teve média de cerca de 108 unidades por ano no período completo; a comparação mostra diferença de escala, não um déficit anual diretamente medido.
- Política de **articulação federativa**: a base permite contar empreendimentos que registram fontes federais, estaduais e municipais, mas essa contagem não mede os valores financeiros aportados por cada esfera.

## Metodologia

1. **Construção do dataset** — curadoria manual de fontes públicas (Prefeitura, MT Par/SiHab-MT, Ministério das Cidades, Caixa), já que não existe base estruturada de habitação municipal. Cada registro tem a URL da fonte.
2. **Análise de entregas** — unidades entregues por ano, com distinção rigorosa entre entregue, em obra e previsto (para não inflar números).
3. **Composição** — por tipo de moradia, faixa de renda e fonte de recurso, filtrando o escopo social estrito.
4. **Contextualização da demanda** — compara a fila histórica e a demanda anual projetada sem inferir cobertura da fila ou déficit residual quando não há dados que liguem famílias atendidas às unidades entregues.

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

- **Escopo:** o indicador principal considera apenas habitação de interesse social no escopo estrito. O empreendimento Parque Primavera, com 171 unidades em obra, está marcado fora desse escopo e é excluído dos totais principais.
- **Dataset curado manualmente** — auditável (toda linha tem fonte), mas pode não capturar todos os empreendimentos.
- **Fila de espera é um ponto único (2021)** — série histórica exigiria pedido via LAI. Sem dados que liguem unidades entregues a famílias atendidas, não calculamos percentual de cobertura pela divisão dos totais.
- **Investimento incompleto** — só o Vida Nova II tem valor consolidado; os demais exigiriam consulta a licitações.
- **Obra ≠ entrega** — o pipeline é oferta potencial sujeita a atrasos.
- **Escopos diferentes na comparação** — a projeção populacional estima demanda habitacional total, enquanto este projeto mede a oferta de habitação social. A diferença é contextual, não um cálculo direto de déficit social.

## Fontes dos dados

Prefeitura de Lucas do Rio Verde, MT Par / SiHab-MT (Sistema de Habitação de Mato Grosso), Ministério das Cidades e Caixa Econômica Federal. URLs individuais na coluna `fonte_url` de cada dataset.

---

**Autora:** Thamires Martins da Silva
Projeto de portfólio em análise de dados — Camada 2 de 2.
