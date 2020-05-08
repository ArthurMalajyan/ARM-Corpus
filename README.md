# Paraphrase-detection

Այստեղ նկարագրված են Ռուսերենի և Հայերենի համար պարաֆրազը հայտնաբերող մոդելներ՝ Rus_bert և Arm_bert: Որոնք համապատասխանաբար ստացվել են [Deeppavlov](http://deeppavlov.ai/) կողմից ստեղծված [RUBERT](http://docs.deeppavlov.ai/en/master/features/models/bert.html)-ի և [Google resarch](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) - կողմից ստեղծված [multilingual BERT](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) ի վրա նուրբ կարգավորման արդյունքում։ 

Ստեղծվել է նոր կորպուս Ռուսերենում պարաֆրազի հայտնաբերման համար։ Որից հետո տվյալները ավելացվել են ռուսերենի հիմնական  կորպուսին պարաֆրազը հայտնաբերելու համար՝ Paraphraser.ru-ին։

|Cotpusis|Paraphraser.ru|Our data|Paraphraser.ru + Our data|
|  :---: |     :---:    | :---:  |          :---:          |
|Train   | 7202         |9364    |13609                    |
|Test    | 1899         |1855    |1899                     |

Որոշ կորպուսներում հեռացվել են բոլոր կետադրական նշանները հասկանալու համար, թե որքանով են ազդում կետադրական նշանները մոդելի աշխատանքի վրա։ Ստեղծված կորպուսները օգտագործելով կատարվել է նուրբ կարգավորում RUBERT-ի վրա։ Ստացվել են հետևյալ արդյունքները՝

|Train|Paraphraser.ru test_data|Our test_data|Paraphraser.ru + Our test_data|
|  :---: |     :---:    | :---:  |          :---:          |
|        | F1  /  Acc      |  F1  /  Acc    |     F1  /  Acc  |
|Paraphraser.ru   |87.9  /  84.9        |80.13  /  71.05    |77  /  69.11             |
|Our data    | 77  /  66         |80.39  /  70.03    |74.96  /  66.9    |
|Paraphraser.ru + Our data   | 87.96  /  85.2         |76.74  /  68.79    |73.29  /  66.36   |

