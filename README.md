# 🚀 Projeto DataScience - Finanças 💰

## Artigo completo de como foi construido a solução:

- Clique no [Link para abrir o artigo](https://medium.com/@weber.cg/an%C3%A1lise-de-sentimento-de-not%C3%ADcias-para-predi%C3%A7%C3%A3o-dos-valores-de-a%C3%A7%C3%B5es-da-petrobras-496260794abc)

## Projeto: **Daily News for Stock Market Prediction**

Solução que use dados textuais de notícias para estimar um comportamento futuro do mercado de ações.
NLP + Classificação

# Repositório V1.0 - Projeto
- Coleta de dados financeiros: [engenharia de dados/Coleta de precos de ativos - YFinance.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20precos%20de%20ativos%20-%20YFinance.ipynb)
- Coleta de dados de noticias: [Coleta de noticias - engenharia de dados/GoogleNews.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20noticias%20-%20GoogleNews.ipynb)
- Experimentos para features engineering: [datasets e notebooks/Experimentos - Analise, feature engineering e selecao de features.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Analise%2C%20feature%20engineering%20e%20selecao%20de%20features.ipynb)
- Experimentos e Tunning Modelos: [datasets e notebooks/Experimentos - Machine Learning.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Machine%20Learning.ipynb)
- Validação estatística modelos: [datasets e notebooks/Predicoes 2022 com modelos treinados de 2021 e 2020.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Predicoes%202022%20com%20modelos%20treinados%20de%202021%20e%202020.ipynb)
- Modelo final: [engenharia de dados/modelos/modelo-Ensemble.pkl](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/modelos/modelo-Ensemble.pkl)


# Repositório V2.0 - Projeto
O projeto passou por uma reestruturação e foi elaborado uma Versão 2.0 para contornar problemas de estabilidade e performance em dados de produção:

- Coleta de dados financeiros: [engenharia de dados/Coleta de precos de ativos - YFinance.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20precos%20de%20ativos%20-%20YFinance.ipynb)
- Coleta de dados de noticias: [Coleta de noticias - engenharia de dados/GoogleNews.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20noticias%20-%20GoogleNews.ipynb)
- Notebook Projeto V 2.0: [V2.0 do Projeto](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Notebook%20final%20-%20V2%20-%20Compilado%20experimentos%20.ipynb)

# Contribuidores: 

1. [Weber Cordeiro](https://github.com/webercg);
2. [Lenon Borges](https://github.com/lenonborges);
3. [Felipe](https://github.com/felipeps1)
4. [Mario]()
5. [Anderson Miranda](https://github.com/aluipio)

# Fonte de dados  

WebScrapping: As noticias foram coletadas utilizando-se API GoogleNews. 

WebScrapping: Os dados financeiros da biblioteca YFinance  

# Metodologia

Os resultados das ações da Petrobras e de noticias relacionadas ao ativo foram consolidadas em um único dataset, adicionando-se rotulos:
  
0 - dias em que ocorreu a queda do valor das ações  
1 - dias com alta das ações  
  
Os titulos de noticias foram concatenados por dia, além disso, as noticias vinculadas em dias sem pregões foram atribuidas ao próximo dia com pregão. Foi gerado um conjunto de 11 features para realizar analise de sentimento utilizando os modelos:
  
Supervisionados:  
Tradução noticias + roBERTa: 3 features  
Tradução noticias + finBERT: 3 features  
  
Não Supervisionados  
Sentilex: 1 feature  
Tradução noticias + VaderSentiment: 4 features  

Feature Engineering:  
Foi conduzido uma batelada de experimentos com variações do dicionário lexico Sentilex realizando análise de palavras mais frequentes em 2020 e 2021 e calculando o enviesamento positivo / negativo ( relação entre a quantidade de ocorrência das palavras em dias com alta/queda das ações sobre ocorrência total ).
  
Testou-se as taxas de inviesamento de 65%, 70%, 75% e 80% e inputação de polaridade de +-1, +-2, +-3, +-4 e +-5.
O dicionário que melhor performou na tarefa de classificação foi o composto pelas palavras com 70% de inviesamento e polaridade de +-3.
  
Para predizer o comportamento do mercado em cada dia, foi considerado, além das features do dia atual as features de até 4 dias anteriores totalizando 55 features.
    
Para selecionar as features foi realizado análise de correlação de variáveis e efetuado experimentos para validar os resultados avaliando a acurácia em 29 modelos ingênuos de classificação utilizando a biblioteca LazyPredict.
  
# Resultados:  
  
O modelo composto pelo ensemble dos 4 melhores modelos atingiu:  
  
- acurácia de 73% sobre os dados de 2020 e 2021;   
- recall de 73% para classe 0;  
- recall 73% para classe 1.  
  
Após retreinar o modelo com os primeiros 3 meses de 2022 o modelo passou a performar com acurácia de 66% sobre os dados de 2022.  

# Melhorias, Gaps do projeto e orientações para manutenção do modelo.  
  
O modelo foi construido para prever os dados de 2020 e 2021 utilizando as palavras inviesadas positivamente e negativamente mais frequentes no período. Dessa forma, para evitar que o modelo fique obsoleto é necessário realizar a atualização do dicionário léxico periodicamente analisando as palavras mais frequentes e inputando a polaridade de +-3 ao dicionário.
  
Além disso, orientamos retreinar o modelo quando observado baixa acurácia nos ultimos 30 dias sem retreino para forçar a aprendizagem de novos exemplos (como ocorrido nos três primeiros meses de 2022). Contudo, uma frequência de retreino de 90 dias já é o suficiente para manter a performance do modelo caso seja observado acurácia de 60% ou superior.
  
Embora tenha sido observado alta acurácia sobre as predições dos dados de validação de 2022, o recall para as classes 0 e 1 ficaram desbalanceados. Isso requer uma nova batelada de experimentos sobre os dados de 2022 para avaliar o motivo desse comportamento e possíveis ajustes no modelos. 
  
# Links Úteis  

- [Trello](https://trello.com/b/oWJT0AQw/stack-labs-3-edi%C3%A7%C3%A3o)
- [Stack Academy](https://stackacademy.com.br)
- [Google COLAB](https://colab.research.google.com/?hl=pt_BR)
- [Kaggle - Dataset](https://www.kaggle.com)


# Abordagem Data Science  
- https://towardsdatascience.com/all-you-need-to-know-about-text-preprocessing-for-nlp-and-machine-learning-bc1c5765ff67

