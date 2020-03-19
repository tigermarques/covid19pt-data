# 😷️🇵🇹 Dados relativos à pandemia COVID-19 em Portugal 

📅️ **Última actualização**: 19 de Março de 2020, 17h30

ℹ️ **Fonte dos dados**: [Direcção Geral de Saúde](https://www.dgs.pt/) - Ministério da Saúde Português, através do _dashboard_ do COVID-19 ([aqui](https://covid19.min-saude.pt/ponto-de-situacao-atual-em-portugal/)  e dos [relatórios de situação publicados diariamente](https://covid19.min-saude.pt/relatorio-de-situacao/) desde 03/03/2020.

👁️ **Utilizaste estes dados para análises/plataformas/notícias?**: Deixa-nos detalhes [aqui](https://github.com/dssg-pt/covid19pt-data/issues/20).

# 🤔 Contexto

Embora a comunicação e partilha de dados por parte do Ministério de Saúde Português tenha melhorado consideravelmente ao longo da crise do COVID-19, ainda está longe de ideal (havendo a destacar o exemplo do [repositório da Protecção Civil Italiana no GitHub](https://github.com/pcm-dpc/COVID-19)).

A informação disponibilizada pela Direcção Geral de Saúde (DGS), para além de não ter o nível de granularidade da das autoridades italianas, também não é disponibilizada em formatos abertos e facilmente inspeccionáveis/manipuláveis. Ficam assim dificultadas tarefas de análise, modelação e visualização por parte da comunidade (quer mais informal, quer mais académica/industrial) disposta a colaborar no combate à pandemia com as ferramentas que conhece: as de análise de dados.

❗ O compromisso deste repositório é justamente esse: **todos os dias enquanto esta pandemia durar, o ficheiro `data.csv` será actualizado com a informação mais recente disponibilizada pela Direcção Geral de Saúde**. Esta informação será extraída do relatório de situação o mais rapidamente possível após a sua disponibilização (que costuma ser ~12h00 GMT+00:00). 

A estrutura base deste ficheiro, desenhada para fácil manipulação em Excel/Python/R não mudará, podendo a comunidade analítica considerá-lo um alvo imutável (em termos de localização e estrutura) para, por exemplo, alimentar plataformas de visualização/modelação. De notar que, mediante a evolução do formato dos relatórios de situação, poderão ser adicionadas novas colunas, mantendo-se claro a retrocompatibilidade. Fontes adicionais de dados poderão também ser adicionadas.

_Porque tudo começa com bons dados._

# 🧱 Estrutura

O repositório está organizado da seguinte forma:
+ `data.csv`: o Pastel de Nata. 
+ `archive/`: arquivo de todos os relatórios de situação disponibilizados pela DGS, em formato `.pdf`. Os relatórios são disponibilizados diariamente, desde o dia 03-03-2020.
+ `notebooks/`: contém um _notebook_ Python com um exemplo simples de como carregar e visualizar os dados.
+ `extra/`: contém fontes de dados extras que podem ser usadas para complementar as análises dos restantes dados. As descrições dessas fontes de dados encontram-se dentro de um README nessa pasta. 

# 📔 Dicionário dos dados

Uma explicação do conteúdo em `data.csv`. 

📝 _ARS_: Administração Regional de Saúde 

| Nome da coluna        | Significado           | Possíveis valores  |
| ------------- |:-------------:| -----:|
| `data` | Data da publicação dos dados | DD-MM-YYYY |
| `data_dados` | Data e hora da recolha dos dados apresentados (quando omitida nos relatórios, assume-se como sendo a data da publicação dos dados) | DD-MM-YYYY HH:MM|
| `confirmados` | Casos confirmados      | Inteiro >= 0 |
| `confirmados_arsnorte` | Casos confirmados na ARS Norte      | Inteiro >= 0 |
| `confirmados_arscentro` | Casos confirmados na ARS Centro      | Inteiro >= 0 |
| `confirmados_arslvt` | Casos confirmados na ARS Lisboa e Vale do Tejo      | Inteiro >= 0 |
| `confirmados_alentejo` | Casos confirmados na ARS Alentejo     | Inteiro >= 0 |
| `confirmados_arsalgarve` | Casos confirmados na ARS Algarve    | Inteiro >= 0 |
| `confirmados_acores` | Casos confirmados na Região Autónoma dos Açores | Inteiro >= 0 |
| `confirmados_madeira` | Casos confirmados na Região Autónoma da Madeira  |  Inteiro >= 0 |
| `confirmados_estrangeiro` | Casos confirmados no estrangeiro | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_novos` | Número de novos casos confirmados comparativamente ao dia anterior. É uma coluna calculada a partir da diferença nos casos `confirmados` entre dias consecutivos. | Inteiro >= 0 |
| `recuperados` | Total de casos recuperados | Inteiro >= 0 |
| `obitos` | Total de óbitos | Inteiro >= 0 |
| `internados` | Número de pacientes COVID-19 internados | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `internados_uci` | Número de pacientes COVID-19 internados em Unidades de Cuidados Intensivos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `lab` | Número de casos suspeitos a aguardar resultados laboratoriais | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `suspeitos` | Total de casos suspeitos (tendo a [definição sido actualizada](https://www.dgs.pt/directrizes-da-dgs/orientacoes-e-circulares-informativas/orientacao-n-002a2020-de-25012020-atualizada-a-250220201.aspx) a 29/02/2020) desde 01/01/2020  | Inteiro >= 0 |
| `vigilancia` | Número de casos sob vigilância pelas autoridades de saúde | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `n_confirmados` | Número de casos cuja suspeita de infecção não se confirmou | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `cadeias_transmissao` | Número de cadeias de transmissão do SARS-CoV-2 activas | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `transmissao_importada` | Número de casos confirmados com transmissão por via de infectados de outros países | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_0_9_f` | Número de casos confirmados do sexo feminino na faixa etária 0-9 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_0_9_m` | Número de casos confirmados do sexo masculino na faixa etária 0-9 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_10_19_f` | Número de casos confirmados do sexo feminino na faixa etária 10-19 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_10_19_m` | Número de casos confirmados do sexo masculino na faixa etária 10-19 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_20_29_f` | Número de casos confirmados do sexo feminino na faixa etária 20-29 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_20_29_m` | Número de casos confirmados do sexo masculino na faixa etária 20-29 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_30_39_f` | Número de casos confirmados do sexo feminino na faixa etária 30-39 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_30_39_m` | Número de casos confirmados do sexo masculino na faixa etária 30-39 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_40_49_f` | Número de casos confirmados do sexo feminino na faixa etária 40-49 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_40_49_m` | Número de casos confirmados do sexo masculino na faixa etária 40-49 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_50_59_f` | Número de casos confirmados do sexo feminino na faixa etária 50-59 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_50_59_m` | Número de casos confirmados do sexo masculino na faixa etária 50-59 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_60_69_f` | Número de casos confirmados do sexo feminino na faixa etária 60-69 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_60_69_m` | Número de casos confirmados do sexo masculino na faixa etária 60-69 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_70_79_f` | Número de casos confirmados do sexo feminino na faixa etária 70-79 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_70_79_m` | Número de casos confirmados do sexo masculino na faixa etária 70-79 anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_80_plus_f` | Número de casos confirmados do sexo feminino na faixa etária 80+ anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_80_plus_m` | Número de casos confirmados do sexo masculino na faixa etária 80+ anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_80_plus_m` | Número de casos confirmados do sexo masculino na faixa etária 80+ anos | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_tosse` | Percentagem de casos infetados que reportaram o sintoma de tosse | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_febre` | Percentagem de casos infetados que reportaram o sintoma de febre | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_dificuldade_respiratoria` | Percentagem de casos infetados que reportaram o sintoma de dificuldade respiratória | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_cefaleia` | Percentagem de casos infetados que reportaram o sintoma de cefaleia ou dores de cabeça | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_dores_musculares` | Percentagem de casos infetados que reportaram o sintoma de dores musculares | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `sintomas_fraqueza_generalizada` | Percentagem de casos infetados que reportaram o sintoma de fraqueza generalizada | fracção entre [0, 1] ou _vazio_ para os dias em que a DGS não reportava este indicador |
| `confirmados_f` | Número total de confirmados do sexo feminino | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava directamente este indicador 
| `confirmados_m` | Número total de confirmados do sexo masculino | Inteiro >= 0 ou _vazio_ para os dias em que a DGS não reportava directamente este indicador 

> Definições exactas de alguns destes termos constam do glossário do [Plano Nacional de Preparação e Resposta à Doença por novo coronavírus (COVID-19)](https://covid19.min-saude.pt/wp-content/uploads/2020/03/Plano-de-Conting%C3%AAncia-Novo-Coronavirus_Covid-19.pdf) (página 65 em diante).

Uma outra métrica com potencial interesse científico, o número de casos com base na data de início de sintomas, é também reportada pela DGS. No entanto, é apenas disponibilizado um gráfico de eixos esparsos, o que pode introduzir erros de aproximação na transcrição e comprometer a factualidade dos dados. Por essa razão, esta informação é propositadamente excluída. 


# 💡 Problemas, inconsistências e melhorias

Quaisquer sugestões de dados complementares (provenientes de fontes oficiais), inconsistências nos dados ou melhorias genéricas, à vontade ➡️ _Issues_ ou _Pull Requests_.

# 🌍 Sobre a Data Science for Social Good Portugal

A [Data Science for Social Good Portugal](https://www.dssg.pt) é uma comunidade aberta de cientistas de dados, amantes de dados e entusiastas de dados que querem atacar problemas que importam verdadeiramente. Acreditamos no poder dos dados para transformar a nossa sociedade para o melhor e para todos.

[@dssgPT](https://twitter.com/dssgpt) | [fb.com/DSSGPortugal](https://www.facebook.com/DSSGPortugal/) | [Instagram @dssg_pt](www.instagram.com/dssg_pt/) | [LinkedIn](https://www.linkedin.com/company/dssg-portugal)
