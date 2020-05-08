# Paraphrase-detection

Այստեղ նկարագրված են Ռուսերենի և Հայերենի համար պարաֆրազը հայտնաբերող մոդելներ՝ Rus_bert և Arm_bert: Որոնք համապատասխանաբար ստացվել են [Deeppavlov](http://deeppavlov.ai/) կողմից ստեղծված [RUBERT](http://docs.deeppavlov.ai/en/master/features/models/bert.html)-ի և [Google resarch](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) - կողմից ստեղծված [multilingual BERT](https://github.com/google-research/bert?fbclid=IwAR2GSNQ7pwjglLqVGOB5PTxlMQ5SgWQZl4x5ZMlda5zArwxo4pp2Z6rp43g) ի վրա նուրբ կարգավորման արդյունքում։ 

Ստեղծվել է նոր կորպուս Ռուսերենում պարաֆրազի հայտնաբերման համար։ Որից հետո տվյալները ավելացվել են ռուսերենի հիմնական  կորպուսին պարաֆրազը հայտնաբերելու համար՝ Paraphraser.ru-ին։

|Cotpusis|Paraphraser.ru|Our data|Paraphraser.ru + Our data|
|  :---: |     :---:    | :---:  |          :---:          |
|Train   | 7202         |9364    |13609                    |
|Test    | 1899         |1855    |1899                     |

Paraphraser.ru - համարվում է ռուսերենի հիմնական  կորպուսը պարաֆրազը հայտնաբերելու համար, որի հիման վրա գնահատում են մոդելի աշխատանքը։

