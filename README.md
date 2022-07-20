# 🚀 Projeto DataScience - Finanças 💰


## Projeto: **Daily News for Stock Market Prediction**

Solução que use dados textuais de notícias para estimar um comportamento futuro do mercado de ações.
NLP + Classificação

# Repositório
- Coleta de dados financeiros: [engenharia de dados/Coleta de precos de ativos - YFinance.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20precos%20de%20ativos%20-%20YFinance.ipynb)
- Coleta de dados de noticias: [Coleta de noticias - engenharia de dados/GoogleNews.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/Coleta%20de%20noticias%20-%20GoogleNews.ipynb)
- Experimentos e features engineering: [datasets e notebooks/Experimentos - Analise, feature engineering e selecao de features.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Analise%2C%20feature%20engineering%20e%20selecao%20de%20features.ipynb)
- Tunning Modelos: [datasets e notebooks/Experimentos - Machine Learning.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Machine%20Learning.ipynb)
- Validação estatística modelos: [datasets e notebooks/Predicoes 2022 com modelos treinados de 2021 e 2020.ipynb](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/datasets%20e%20notebooks/Experimentos%20-%20Predicoes%202022%20com%20modelos%20treinados%20de%202021%20e%202020.ipynb)
- Modelo final: [engenharia de dados/modelos/modelo-Ensemble.pkl](https://github.com/webercg/NLP---Daily-News-for-Stock-Market-Prediction/blob/main/engenharia%20de%20dados/modelos/modelo-Ensemble.pkl)

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

Para predizer o comportamento do mercado em cada dia, foi considerado, além das features do dia atual as features de até 4 dias anteriores totalizando 55 features:
  
Utilizamos análise de correlação para selecionar as features validando avaliando a acurácia do modelo de classificação em 29 algorítmos ingênuos utilizando a biblioteca LazyPredict.
  
# Resultados:  
  
O modelo composto pelo ensemble dos 4 melhores modelos atingiu:  
  
- acurácia de 73% sobre os dados de 2020 e 2021;   
- recall de 73% para classe 0;  
- recall 73% para classe 1.  
  
Após retreinar o modelo com os primeiros 3 meses de 2022 o modelo passou a performar com acurácia de 66% sobre os dados de 2022.  

# Melhorias, Gaps do projeto e sugestões.  
  
O modelo foi construido para prever os dados de 2020 e 2021 utilizando as palavras mais frequentes em noticias daquele ano e adicionando-as ao dicionário léxico Sentilex com polaridade de +-3. Dessa forma, para evitar que o modelo fique obsoleto é necessário realizar periodicamente a análise de palavras mais frequentes e adicioná-las ao léxico do dicionário Sentilex inputando uma polaridade de +-3. 
  
Além disso, orientamos retreinar o modelo se observado baixa acurácia nos próximos 30 dias sem retreino para forçar a aprendizagem de novos exemplos (como ocorrido nos três primeiros meses de 2022). Se o modelo performar com acurácia de 60% ou superior uma frequência de retreino de 90 dias já é o suficiente para mantê-lo nesse patamar.
  
Embora tenha sido observado alta acurácia sobre as predições dos dados de validação de 2022, observamos também que o recall da classe 0 e classe 1 ficaram desbalanceados. Isso requer uma nova batelada de experimentos sobre os dados de 2022 para avaliar o motivo desse comportamento e possíveis ajustes no modelos. 
  
# Links Úteis  

- [Trello](https://trello.com/b/oWJT0AQw/stack-labs-3-edi%C3%A7%C3%A3o)
- [Stack Academy](https://stackacademy.com.br)
- [Google COLAB](https://colab.research.google.com/?hl=pt_BR)
- [Kaggle - Dataset](https://www.kaggle.com)


# Abordagem Data Science  
- https://towardsdatascience.com/all-you-need-to-know-about-text-preprocessing-for-nlp-and-machine-learning-bc1c5765ff67

