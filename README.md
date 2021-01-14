# Big_Data
# importation des librairies
import numpy as np
import math
from random import random
from pyspark import SparkContext, SparkConf 
from pyspark.sql import SparkSession
from operator import add
from time import time

#ouverture de la session Spark
conf = pyspark.SparkConf().setAppName('pi_estimator').setMaster('local')
sc = pyspark.SparkContext(conf = conf)

#fonction qui permet de simuler un point p avec deux coordonnées x et y pour déterminer si le point simulé est à l’intérieur ou à l'extérieur du cercle
def is_point_inside_unit_circle(p):
    x, y = random(), random()
    if x*x + y*y < 1:
      return 1
    else: 
      return 0

#tester et afficher les points de la fonction avec p=10
print(is_point_inside_unit_circle(10))

#fonction avec spark pour estimer la valeur de pi 
def pi_estimator_spark(n):
    count = sc.parallelize(range(0, n)).map(is_point_inside_unit_circle).reduce(add)
    #estimer pi
    pi= (4*count)/n
    return pi   

#fonction avec numpy pour estimer la valeur de pi
def pi_estimator_numpy(n):  
    n_in=0
    for i in range(n):
        point = is_point_inside_unit_circle(1)
        if point == 1:
            n_in += 1

    pi=(4*n_in)/n            
    return pi


# initialisation de n   
n=100000

#execution de la fonction spark et mesure du temps d'éxecution
tempDebut=time.time()
estimateur_pi_spark=pi_estimator_spark(n)
tempFin=time.time()

#Temps d'éxecution avec spark
temp_spark=tempFin-tempDebut

 #affichage temps exécution et valeur d'estimation de pi
print("Temps d'execution avec Spark :", temp_spark)
print("La valeur approchée de Pi avec spark est:",estimateur_pi_spark)

#execution de la fonction spark et mesure du temps d'éxecution
tempDebut=time.time()
estimateur_pi_numpy=pi_estimator_numpy(n)
tempFin=time.time()

#Temps d'éxecution avec spark
temp_numpy=tempFin-tempDebut

 #affichage temps exécution et valeur d'estimation de pi
print("Temps d'execution avec Spark :", temp_numpy)
print("La valeur approchée de Pi avec spark est:",estimateur_pi_numpy)
