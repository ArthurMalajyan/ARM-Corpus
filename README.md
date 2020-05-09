# Paraphrase-detection

Here are described Russian and Armenian paraphrases detection 2 models. Which, accordingly, were obtained by fine-tuning [Deeppavlov's](http://deeppavlov.ai/) [RUBERT](http://docs.deeppavlov.ai/en/master/features/models/bert.html) and [Google resarch's](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) [multilingual BERT](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g)  


## Russian paraphrase detection model
Created new Corpus for Russian paraphrase detection. After that, the data was added  to [Paraphraser.ru](http://paraphraser.ru/) (the main Russian corpus of paraphrase detection).

|Corpuses|Paraphraser.ru|Our data|Paraphraser.ru + Our data|
|  :---: |     :---:    | :---:  |          :---:          |
|Train   | 7202         |9364    |13609                    |
|Test    | 1899         |1855    |1899                     |

In some cases, all punctuation marks have been removed to understand how punctuation affects the work of the model. Using the created corpuses, was made fine tuning on the RUBERT.

|Train|Paraphraser.ru test_data|Our test_data|Our test_data without punctuation|
|  :---: |     :---:    | :---:  |          :---:          |
|        | F1   /   Acc      |  F1  /  Acc    |     F1  /  Acc  |
|Paraphraser.ru   |87.9    /    84.9        |80.13  /  71.05    |77  /  69.11             |
|Our data    | 77  /  66         |80.39  /  70.03    |74.96  /  66.9    |
|Paraphraser.ru + Our data   | 87.96  /  85.2         |76.74  /  68.79    |73.29  /  66.36   |


## Armenian paraphrase detection model
Armenian paraphrase detection model is a new paraphrase detection model for Armenian sentences which obtains state-of-the-art result.

For Armenian has been created paraphrase Detection Corpus, which did not exist before․ Were taken Hetq and Panarmenian news websites articles from the last 10 years. In the initial step, the pairs of paraphrase sentences were obtained by comparing the sentences of the taken articles with each other. As a result were selected, the sentences whose

1. Overlap coefficient >= 0.5.
2. levenshtein distance <= 50.
3. The number of words in a sentence is greater than 6 and less than 22.

In the obtained sentences were few differences between the words in the paraphrase sentences, mostly the same words were used. Այդ իսկ պատճառով վերցված հոդվածների նախադասությունները թարգմանվեցին Անգլերեն,ապա ստացված անգլերեն նախադասությունները նորից թարգմանվեցին Հայերեն։ Թարգմանված նախադասությունները համեմատելով օրիգինալ նախադասությունների հետ նկատվեց, որ նախադասությունների մեծ մասը պարաֆրազ էր։Ավելի լավ արդյունք ստանալու համար թարգմանված նախադասությունների զույգերը տրվեցին լեղվաբաններին , ովքեր կատարեցին նշումներ և ստացվեցին հետևյալ աորդյունքները․

|number of examples|all|strict paraphrases|loose paraphrases|non-paraphrases|
|  :---: |     :---:    | :---:  |          :---:          | :---:  |
|Train   | 4233         |1339   |2683               | 211 |
|Test    | 2325         |709   |1521                  | 95 |


Ստեղծված test-ը թարգմանվել է անգլերեն և ռուսերեն ՝ փորձելու համար, թե ինչ արդյունքներ կստացվեն Paraphraser.ru Train-ի և [MRPC](https://www.microsoft.com/en-us/download/details.aspx?id=52398) Train-ի վրա։ Նաև Paraphraser.ru Train-ը և MRPC Train-ը թարգմանվել են հայերեն ,յուրաքանչյուրի համար կատարվել է նուրբ կարգավորում multilingual BERT-ի վրա։ 

|Models Results|   F1   |  Acc.     |
|  :---: |     :---:    |     :---:    |
|multilingual BERT trained on Paraphraser.ru Train data transleted into Armenian and tested on our test data | 78.98  | 84.32  |
|multilingual BERT trained on MRPC Train data transleted into Armenian and tested on our test data   | 46.8        | 30.55 |
|RUBERT tested on our test data translated into Russian| 68.34         | 73.59  |
|BERT trained on MRPC Train data and tested on our test data translated into English | 83.24  |  88.47     |
|multilingual BERT trained on our Train data and tested on our test data| 83.8    |  89.06   |




