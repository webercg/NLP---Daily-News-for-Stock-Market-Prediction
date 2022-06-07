# 📝 **Caderno de anotações** 🤓

## Projeto: **Daily News for Stock Market Prediction** 🚀

- [Proposta de Data Source - Kaggle](https://www.kaggle.com/datasets/aaron7sun/stocknews)


## Fontes Alteranativas:

1. Google News;
2. Twitter;


## Ambitos jornalisticos:

- [Exame - Finanças](https://exame.com/noticias-sobre/financas/)
- [Money Times](https://www.moneytimes.com.br/)
- [Info Money](https://www.infomoney.com.br)
- [Invest News](https://investnews.com.br/)
- [Investing](https://br.investing.com/)
- [Suno](https://www.suno.com.br)
- [The Capital Advisor](https://comoinvestir.thecap.com.br/)

## Dicionários léxicos

Para determinar a polaridade, positividade e negatividade de uma noticia é possível utilizar dois tipos de algorítmos: Supervisionados e não supervisionados.

### Não supervisionados: Não necessitam de noticias rotuladas e nem de treinamento

Os modelos não supervisionados utilizam-se de dicionários Léxicos, onde cada palavra detém um valor único de polaridade, subjetividade, positividade e negatividade. Há diversos dicionários temáticos disponíveis para uso (Finanças, Pesquisa, Saúde, Etc), a maioria dos dicionários não possuem suporte para o idioma português. 
Há um dicionário Léxico BBLEX de finanças em portugues/inglês criado por pesquisadores da UTFPR, contudo não foi disponibilizado o dicionário para consumo.

Fonte: https://www.brazilianjournals.com/index.php/BRJD/article/view/23958/19223
Nota 1: Infelizmente não encontrei o BBLEX para uso. ( Entrar em contato com os autores? )

Nota 2: Há um dicionário SentilexPT disponível em português, no entanto não é específico para finanças como o BBLEX.

Há diversas opções em ingles, por exemplo, nesse artigo há uma comparação entre diversos algorítmos que calculam a polaridade, negatividade e positividade de noticias rotuladas.  
https://dl.acm.org/doi/abs/10.1145/2512938.2512951 
No geral, o metodo SentiStrength perfomou melhor que outros 7 metodos (PANAS-t, Emoticons, SASA, SenticNet, Happiness Index, SentiWordNet, LIWC).  Com revocação 76,7%, acurácia 81,5% e F1score de 0.765.  

### Supervisionados: Necessitam de noticias pré-rotuladas para o treinamento do modelo.

Necessita de trabalho manual para rotular as noticias entre positiva, negativa e neutra.
