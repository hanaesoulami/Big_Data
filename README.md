# Big_Data
#commande pour éxecuter le programmme
./spark-submit pi_estimator.py

#Affichage résultat
# pour n=100000
![Capture d’écran 2021-01-14 150638](https://user-images.githubusercontent.com/74453506/104602539-cb7f0f00-567b-11eb-9f58-28881faa5d85.png)

![100000tab](https://user-images.githubusercontent.com/74453506/104604956-34678680-567e-11eb-94d3-6710975fc1c7.png)


# pour n=1000000
![1000000](https://user-images.githubusercontent.com/74453506/104602521-c6ba5b00-567b-11eb-860e-2a969a736d2c.png)

![10000000tab](https://user-images.githubusercontent.com/74453506/104604981-39c4d100-567e-11eb-9b3c-4d202ee67e03.png)

#Remarque:

On remarque que pour n=100000 ,numpy donne une meilleure estimation de pi avec moins de temps de calcul que spark, on remarque la meme chose pour n=1000000 sauf que le valeur d'estimation de pi est plus précise avec un nombre de n plus grand.
