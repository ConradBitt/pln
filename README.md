# Processamento de Linguagem Natural


## [Análise de sentimento](https://github.com/ConradBitt/processamento_linguagem_natural/blob/master/PLN.ipynb)

Vou abordar o conteito de processamento de linguagem natural ou PLN. Esta é uma das técnicas que o Google utiliza para interpretar o que foi escrito na barra de busca dele. Geralmente outros buscadores fazem isto também, mas o google é o mais utilizado.

Como ele faz para entender o que você esta querendo dizer?? Bom: Processamento de Linguagem Natural. Com a PLN o google pode trazer os resultados mais relevantes para sua pesquisa, assim como o Google Home, Alexa ou Siri fazem para entender o que você esta falando... Tudo isso é processamento de linguagem natural.

Vamos iniciar desenvolvendo um analisador de sentimentos através da NPL(Natural Processing Language), mas como isso funciona??

Imagina que você quer assistir um filme então você vai lá e busca criticas sobre o filme por exemplo no site Adoro Cinema. A critica do filme será interpretada por você e aí provavelmente você dará um parecer (mesmo que mentalmente) bom ou ruim, ou talvez com estrelas... E é exatamente isto que nosso algorítmo irá reproduzir: Classificar críticas de filmes, ou seja, analise de sentimento perante um texto com base nos rótulos (estrelas, notas, bom/rum).

Para isso vamos:

* Importar uma base de dados já classificada.
* Criar um modelo de machine learn capaz de interpretar a lingaugem humana e classificar este texto (atráves de WORD CLOUDS).
* Pré processamento de texto para torna-lo mais preciso.
* Usar a distribuição de frequências para ajudar na análise de dados.
* Realizar Tokenização com o NLTK

## [Analise de contexto](https://github.com/ConradBitt/processamento_linguagem_natural/blob/master/Word2Vec_Interpreta%C3%A7%C3%A3o_da_linguagem_com_word_embedding_.ipynb)

Existem algumas tecnicas de representar palavras, frases ou textos através de vetores. As mais famosas são a *one-hot-encoding* que transforma cada palavra em um vetor de base de um espaço vetorial e a *word2vec* que representa a palavra, frase ou texto como um vetor de um espaço vetorial. Na one-hot-encoding se produz matrizes esparsas que podem ter um alto custo computacional, já na representação word2vec os vetores são densos.

As possibilidade que o word2vec proporcional são extremamente importantes para a compreenção de contexto, mas existem duas abordagem. Primeira é a CBOW (*Continous Bag Of Word*) que através de um conjunto de palavras que fornece um contexto tenta estimar outra palavra e a *Skip Gram*, que através de uma palavra tenta estimar o contexto.

Para isso, será realizado os seguintes estudos: 

* Entender as tecnicas one-hot-encoding e word2vec 
* Explorar as formas de usar o word2vec
* Combinação linear de vetores
* Usando CBOW para classificação 
* Usando SkipGram para classificação
* Comparar o desempenho do CBOW/SkipGram em diferentes volumes de dados.

## [Criando um classificador com base em Word2Vec SkipGram / CBOW](https://github.com/ConradBitt/processamento_linguagem_natural/blob/master/Criando_Classificador_com_Word2vec.ipynb)

Diferente do notebook anterior onde foi utilizado o Gensim para importar um modelo já treinado, neste notebook utilizamos o módulo SpaCy para incorporar alguns pre processamentos de textos, em seguida vetorizar as frases atraves das técnicas de Word2Vec Skip Gram e CBOW.

O modelo wor2vec baseado na arquitetura **CBOW** quando aplicado numa classificação categorica teve um **valor preditivo positivo médio 80% e uma sensibilidade de 79%**. Ja o modelo word2vec baseado em uma arquitetura **Skip Gram teve um **valor preditivo positivo ponderado de 82% e uma sensibilidade de 79%**. Isso pode levar a crer que o SkipGram é melhor do que o CBOW, mas esta inferência não é uma verdade absoluta. A arquiteura SkipGram demorou 1h 56min para pré-processar 90mil dados, contra a 1h 46min do CBOW.

Além disso, outra coisa que foi possível verificar no notebook [Word2Vec: Interpretação da linguagem com word embedding](https://github.com/ConradBitt/processamento_linguagem_natural/blob/master/Word2Vec_Interpreta%C3%A7%C3%A3o_da_linguagem_com_word_embedding_.ipynb) é a respeito do desempenho em relação ao tamanho dos dados com quais as arquiteturas lidam, isto é, testamos as arquiteturas prevendo titulos com frases até 10 palavras e com artigos/textos inteiros de jornais. Verifiquei que: **Dada a natureza do SkipGram prever o contexto a traves de uma palavra quando a palavra pertence à um artigo inteiro é relativamente dificil pra esta arquitetura entregar bons resultados. Ja a caracteristica do CBOW de prever uma palavra dado um contexto de uma frase tem um desempenho muito melhor com dados muitos longos.**
