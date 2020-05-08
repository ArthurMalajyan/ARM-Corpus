# Paraphrase-detection

Here are described Russian and Armenian paraphrases detection 2 models, Rus_bert and Arm_bert: Որոնք համապատասխանաբար ստացվել են [Deeppavlov](http://deeppavlov.ai/) կողմից ստեղծված [RUBERT](http://docs.deeppavlov.ai/en/master/features/models/bert.html)-ի և [Google resarch](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) - կողմից ստեղծված [multilingual BERT](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) ի վրա նուրբ կարգավորման արդյունքում։ 


## Rus_bert
Ստեղծվել է նոր կորպուս Ռուսերենում պարաֆրազի հայտնաբերման համար։ Որից հետո տվյալները ավելացվել են ռուսերենի հիմնական  կորպուսին պարաֆրազը հայտնաբերելու համար՝ [Paraphraser.ru](http://paraphraser.ru/)-ին։

|Cotpusis|Paraphraser.ru|Our data|Paraphraser.ru + Our data|
|  :---: |     :---:    | :---:  |          :---:          |
|Train   | 7202         |9364    |13609                    |
|Test    | 1899         |1855    |1899                     |

Որոշ կորպուսներում հեռացվել են բոլոր կետադրական նշանները հասկանալու համար, թե որքանով են ազդում կետադրական նշանները մոդելի աշխատանքի վրա։Ստեղծված կորպուսները օգտագործելով կատարվել է նուրբ կարգավորում RUBERT-ի վրա։ Ստացվել են հետևյալ արդյունքները՝

|Train|Paraphraser.ru test_data|Our test_data|Paraphraser.ru + Our test_data|
|  :---: |     :---:    | :---:  |          :---:          |
|        | F1   /   Acc      |  F1  /  Acc    |     F1  /  Acc  |
|Paraphraser.ru   |87.9    /    84.9        |80.13  /  71.05    |77  /  69.11             |
|Our data    | 77  /  66         |80.39  /  70.03    |74.96  /  66.9    |
|Paraphraser.ru + Our data   | 87.96  /  85.2         |76.74  /  68.79    |73.29  /  66.36   |


## Arm_bert

Հայերենի համար ստեղծվել է մինչև այժմ գոյություն չունեցող պարաֆրազի հայտնաբերման կորպուս։ Վերցվել են Հետք և Պանարմենիա լրագրողական կայքերի վերջին 10 տարվա հոդվածները։ Սկզբնական քայլում պարաֆրազ նախադասությունների զույգերը ստացվել են վերցված հոդվածների նախադասությունների իրար հետ համեմատության արդյունքում։ Վերցվել են այն նախադասությունները՝ որոնց overlap coefficient>=0.5 և levenshtein distance<=50 ից։ Ստացված նախադասություններում քիչ էին պարաֆրազ նախադասությունների բառերի տարբերությունները և հիմնականում նույն բառերն էին օգտագործված։ Այդ իսկ պատճառով վերցված հոդվածների նախադասությունները թարգմանվեցին Անգլերեն,ապա ստացված անգլերեն նախադասությունները նորից թարգմանվեցին Հայերեն։ Թարգմանված նախադասությունները համեմատելով օրիգինալ նախադասությունների հետ նկատվեց, որ նախադասությունների մեծ մասը պարաֆրազ էր։Ավելի լավ արդյունք ստանալու համար թարգմանված նախադասությունների զույգերը տրվեցին լեղվաբաններին , ովքեր կատարեցին նշումներ և ստացվեցին հետևյալ աորդյունքները․

|number of examples|all|strict paraphrases|loose paraphrases|non-paraphrases|
|  :---: |     :---:    | :---:  |          :---:          | :---:  |
|Train   | 4233         |1339   |2683               | 211 |
|Test    | 2325         |709   |1521                  | 95 |


Ստեղծված test-ը թարգմանվել է անգլերեն և ռուսերեն ՝ փորձելու համար, թե ինչ արդյունքներ կստացվեն Paraphraser.ru Train-ի և [MRPC](https://www.microsoft.com/en-us/download/details.aspx?id=52398) Train-ի վրա։ Նաև Paraphraser.ru Train-ը և MRPC Train-ը թարգմանվել են հայերեն ,յուրաքանչյուրի համար կատարվել է նուրբ կարգավորում multilingual BERT-ի վրա։ 

|Models Results|   F1   |  Acc.     |
|  :---: |     :---:    |     :---:    |
|multilingual BERT - ը սովորացված Paraphraser.ru Train -ի Հայերեն թարգմանված տվյալներով և ստուգված մեր test -ի վրա  | 78.98  |  84.32  |
|multilingual BERT - ը սովորացված MRPC Train -ի Հայերեն թարգմանված տվյալներով և ստուգված մեր test -ի վրա   | 46.8        | 30.55 |
|RUBERT-ը փորցարկված ռուսերեն թարկմանված մեր  test -ի վրա    | 68.34         | 73.59  |
| BERT(սովորացված MRPC -ի վրա) և փորցարկված անգլերեն թարկմանված մեր  test -ի վրա   | 83.24  |  88.47     |
|Մեր train -ը փորձարկված մեր test -ի վրա  | 83.8    |  89.06   |





