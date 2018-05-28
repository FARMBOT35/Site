---

layout: post
title:  "Fonctionnement du Farmbot"
date:   2017-12-04
categories: jekyll Cat2
author: "Team Farmbot"

---

<h1 align = "center"> Fonctionnement du Farmbot </h1>

<p> <font color= "#996633">
Le Farmbot est construit en quatre principaux blocs qui sont chacuns reliés entre eux.
Tout d’abord la <strong>“Farmbot Web application”</strong> [1], qui est l’interface permettant à l’utilisateur d'interagir de différentes façons avec le robot. Ensuite, il y a la <strong>partie Raspberry</strong> [2], directement connecté à la web-App. Elle permet de synchroniser chaque demande, chaque nouvelle séquence et de remonter les informations jusqu’à l’utilisateur. Ce bloc est relié à <strong>l’arduino</strong> [3], ce micro-contrôleur permet de contrôler la partie matérielle et de retourner les opérations. </font>
</p>

![Image](/assets/FonctionnementFarmbot.png){: .center-image }

<p> <font color= "#996633">
La structure du Farmbot est composé de 4 grandes parties, la dernière est la partie Farmbot. Ce terme défini en faite le robot en lui même, toutes la partie Hardware connecté à l’arduino.
Nous allons étudier séparément le fonctionnement de chaque blocs.</font>
</p>

<h1 align = "center"> La Web-app </h1>

<p> <font color= "#996633">
Ce que les créateurs du Farmbot appelle la “Web-App” est en réalité l’outil qui sert d’interface entre l’utilisateur et le Farmbot. Cette interface est accessible pour tous les utilisateurs sur le web, sur leurs smartphones et également sur tablette .  La Web-App est de base hébergé sur my.farmbot.io. Cependant, il est possible de l’héberger localement. </font>
</p>
![Image](/assets/WebApp.png){: .center-image }

<p> <font color= "#996633">
Cet outil permet de réaliser des tâches tels que le placement des différentes plantes grâce à un système de glisser-déposer. L’utilisateur a un plan de son jardin et une liste des plantes et légumes à sa disposition. Il lui suffit de glisser la plante qu’il souhaite planter à l’emplacement souhaité. Une fois l’application synchronisé avec le Farmbot, celui-ci va automatiquement planter la graine choisie au bon endroit.
La réalisation d’événement possède des fréquences définies par l’utilisateur. Par exemple, l'utilisateur créé un évènement d’irrigation de son jardin et décide de le mettre en place toutes les semaines le même jour et à la même heur
</font></p>
<p> <font color= "#996633">
L’application web permet d’afficher les informations sur le système et l’état de la connexion entre les différentes parties du Farmbot. Par ailleurs, elle sert à initialiser le robot Farmbot.
On peut définir où sont placées les différentes têtes pour qu’ensuite le bras du Farmbot puisse les utiliser. Une dernière possibilité pour l’utilisateur et de configurer la caméra ainsi que définir la sensibilité à la détection des mauvaises herbes.
</font></p>

<h1 align = "center"> La Raspberry Pi </h1>

![Image](/assets/RPI.jpeg){: .center-image }
<p><font color= "#996633">
<strong>La Raspberry Pi est un élément essentiel au fonctionnement du Farmbot</strong>. En effet, il fait le lien entre la Web-App et la partie Arduino. C’est lui le cerveau du robot. La connexion entre l’application web et la Raspberry Pi se fait en Ethernet ou en Wifi. Dans les deux cas une passerelle MQTT est utilisée. Le serveur MQTT est appelé “broker”. C’est lui qui va collecter les informations. Les clients MQTT, sont abonnés à des topics. Le serveur peut alors envoyer des informations à tous les clients connectés à un même topic.

Cette connexion permet de transférer les commandes désirées par l’utilisateur lorsqu’il réalise par exemple une séquence de plantation ainsi que de faire remonter des informations sur l’état des capteurs.


La Raspberry Pi est connectée au contrôleur Arduino en USB pour lui transmettre les différentes commandes et recevoir des données tels que celles fournies par le capteur de sol.
</font></p>

<h1 align = "center"> L'arduino </h1>

<p><font color ="#996633">
Le contrôleur Arduino ATmega réalise le lien avec la partie mécanique du Farmbot. En fonction des commandes reçues par la Raspberry Pi, il commande les différentes parties du Farmbot. Les moteurs sont dirigés grâce à la carte RAMPS qui est branchée sur l’arduino. Cette carte permet d'interfacer plusieurs fonctionnalités comme la commande de plusieurs moteurs. Le contrôle se fait par envoi d’impulsions électriques, l’Arduino interagit alors avec les moteurs pour déplacer le bras et réaliser l’ensemble des commandes . Pour ce qui est du contrôle et du choix des têtes, cela est réalisé grâce à l’écriture sur les broches (PINs) correspondantes. L’Arduino récolte également les données de ses capteurs pour les transmettre à la Raspberry qui, ensuite, fait remonter les informations à la Web-App via la passerelle MQTT.
</font></p>
