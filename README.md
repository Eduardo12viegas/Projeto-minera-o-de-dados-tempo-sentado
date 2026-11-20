# Tempo sentado e saúde mental em escolares brasileiros

Projeto da disciplina **Mineração de Dados**: agrupamento (K-Means) e regras de associação (Apriori) com os microdados da **Pesquisa Nacional de Saúde do Escolar (PeNSE) 2024**, do IBGE.

**Autores:** Eduardo e Hugo

## Pergunta do projeto
O tempo que o escolar passa sentado por dia (que inclui TV, videogame, computador, celular e tablet, e por isso serve de aproximação para o tempo de tela) está associado a mais indicadores de sofrimento psicológico?

## Base de dados
- Fonte: [IBGE, PeNSE](https://www.ibge.gov.br/estatisticas/sociais/saude/9134-pesquisa-nacional-de-saude-do-escolar.html) (microdados 2024).
- 153.870 registros e 430 colunas; usamos 11 colunas e os 105.039 escolares de 13 a 17 anos com respostas completas.
- **O CSV não está neste repositório** (148 MB, acima do limite de 100 MB por arquivo do GitHub). Baixe-o no site do IBGE e salve como `PENSE2024_MICRODADOS.csv` na mesma pasta do notebook.

## Conteúdo
| Item | Descrição |
|---|---|
| `mineracao_dados_pense2024.ipynb` | Todo o código: pré-processamento, análise exploratória, K-Means e Apriori |
| `relatorio/` | Relatório final (trabalho escrito) |
| `apresentacao/` | Slides da apresentação (27/11, 15 minutos) |
| `figuras/` | Gráficos gerados pelo notebook |
| `resultados/` | Tabelas em CSV geradas pelo notebook |

## Como executar
```bash
pip install pandas numpy matplotlib scikit-learn scipy jupyter
jupyter notebook mineracao_dados_pense2024.ipynb
```
Ajuste `CAMINHO` na primeira célula de código se o CSV estiver em outra pasta. O Apriori é implementado no próprio notebook, sem `mlxtend`.

## Principais resultados
- Entre quem passa **mais de 6 h** sentado por dia, a tristeza chega a 39,5% (contra 25,5% de quem passa até 2 h) e a irritação a 56,6% (contra 36,4%), com porcentagens ponderadas pelo peso amostral.
- **K-Means (K = 4)** encontra quatro perfis: baixo sofrimento, preocupados e irritados, poucos amigos e sofrimento elevado. O tempo sentado médio cresce nos perfis de maior sofrimento.
- **Apriori:** a regra "mais de 6 h sentado → tristeza" tem confiança de 38,9% e lift de 1,35; "mais de 6 h + triste → vida não vale a pena" tem confiança de 51,0% e lift de 2,93.

## Limitações
Estudo transversal (correlação, não causa); o tempo sentado não isola o uso de telas; a correlação geral é pequena (Spearman de 0,14); K-Means e Apriori não usam os pesos amostrais; a separação entre grupos é fraca (silhueta de 0,16).
