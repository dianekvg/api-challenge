

```python
#set dependencies, keys, urls

import pandas as pd
import requests
import json
import matplotlib.pyplot as plt
from citipy import citipy
import numpy as np
import time

file_name = "../../PythonScripts/BootcampExercises/API_Keys/api_keys.json"
data = json.load(open(file_name))
key = data['openweather']
url = "http://api.openweathermap.org/data/2.5/weather?"
units = "imperial"
query_url = url + "appid=" + key + "&units=" + units + "&q="
```


```python
#generate random city name, check for duplicates, check for response; append data to list until there are 500 records

cities = []
city_data = []

while len(city_data) < 500:
    randcity = citipy.nearest_city((np.random.randint(low=-9000, high=9000)*.01), (np.random.randint(low=-18000, high=18000)*.01))
    city = randcity.city_name
    if city not in cities:
            target_url = query_url + city.replace(" ","+")
            response = requests.get(target_url).json()
            cities.append(city)
            if response["cod"] == 200:
                city_data.append(response)
                print("("+str(len(city_data))+")  "+response.get("name")+":  "+target_url)
```

    (1)  Inyonga:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=inyonga
    (2)  Lebu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lebu
    (3)  Plast:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=plast
    (4)  Sao Filipe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sao+filipe
    (5)  Melo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=melo
    (6)  Ushuaia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ushuaia
    (7)  Albany:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=albany
    (8)  Qaanaaq:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=qaanaaq
    (9)  Avarua:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=avarua
    (10)  Mayo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mayo
    (11)  Busselton:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=busselton
    (12)  Barrow:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=barrow
    (13)  Ponta do Sol:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ponta+do+sol
    (14)  Banda Aceh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=banda+aceh
    (15)  Yumen:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yumen
    (16)  Castro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=castro
    (17)  Waipawa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=waipawa
    (18)  Khatanga:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=khatanga
    (19)  Chuy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chuy
    (20)  Brae:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=brae
    (21)  Port Alfred:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=port+alfred
    (22)  Kawalu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kawalu
    (23)  Yellowknife:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yellowknife
    (24)  Jamestown:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=jamestown
    (25)  Saldanha:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saldanha
    (26)  Burlington:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=burlington
    (27)  Cherskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cherskiy
    (28)  Husavik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=husavik
    (29)  Muisne:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=muisne
    (30)  Hermanus:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hermanus
    (31)  Mar del Plata:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mar+del+plata
    (32)  Saint-Leu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint-leu
    (33)  Corinto:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=corinto
    (34)  Punta Arenas:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=punta+arenas
    (35)  Ponta Delgada:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ponta+delgada
    (36)  Amot:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=amot
    (37)  Rikitea:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=rikitea
    (38)  Longyearbyen:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=longyearbyen
    (39)  Ostrovnoy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ostrovnoy
    (40)  El Dorado:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=el+dorado
    (41)  Impfondo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=impfondo
    (42)  Auch:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=auch
    (43)  Chifeng:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chifeng
    (44)  Makakilo City:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=makakilo+city
    (45)  Puerto Escondido:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=puerto+escondido
    (46)  Ghanzi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ghanzi
    (47)  Ipixuna:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ipixuna
    (48)  Astoria:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=astoria
    (49)  Mataura:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mataura
    (50)  Bluff:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bluff
    (51)  Lompoc:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lompoc
    (52)  Bethel:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bethel
    (53)  Ruteng:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ruteng
    (54)  Nikolskoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nikolskoye
    (55)  Grindavik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=grindavik
    (56)  Te Anau:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=te+anau
    (57)  Beringovskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=beringovskiy
    (58)  Narsaq:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=narsaq
    (59)  Diego de Almagro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=diego+de+almagro
    (60)  Christchurch:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=christchurch
    (61)  Inta:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=inta
    (62)  Biak:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=biak
    (63)  Tuatapere:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tuatapere
    (64)  Morwell:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=morwell
    (65)  Ballina:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ballina
    (66)  Chapais:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chapais
    (67)  Vila Velha:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vila+velha
    (68)  Marsh Harbour:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=marsh+harbour
    (69)  Poum:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=poum
    (70)  Knyaze-Volkonskoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=knyaze-volkonskoye
    (71)  Ribeira Grande:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ribeira+grande
    (72)  Gushikawa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gushikawa
    (73)  Sanmenxia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sanmenxia
    (74)  Nanortalik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nanortalik
    (75)  Hobart:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hobart
    (76)  Vaini:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vaini
    (77)  Alvaraes:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=alvaraes
    (78)  Tuktoyaktuk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tuktoyaktuk
    (79)  Yangambi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yangambi
    (80)  Bulawayo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bulawayo
    (81)  Tara:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tara
    (82)  Kapaa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kapaa
    (83)  Tashtagol:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tashtagol
    (84)  Sitka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sitka
    (85)  Saskylakh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saskylakh
    (86)  Bamiantong:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bamiantong
    (87)  Loanda:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=loanda
    (88)  Katsuura:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=katsuura
    (89)  Butaritari:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=butaritari
    (90)  Pangnirtung:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pangnirtung
    (91)  Shimoda:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=shimoda
    (92)  Pimentel:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pimentel
    (93)  Panjab:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=panjab
    (94)  Atuona:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=atuona
    (95)  Cape Town:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cape+town
    (96)  Rumoi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=rumoi
    (97)  Torbay:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=torbay
    (98)  Luwuk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=luwuk
    (99)  Birjand:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=birjand
    (100)  Shahreza:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=shahreza
    (101)  Pisco:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pisco
    (102)  Georgetown:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=georgetown
    (103)  Ayr:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ayr
    (104)  Dikson:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=dikson
    (105)  Bredasdorp:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bredasdorp
    (106)  Komsomolskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=komsomolskiy
    (107)  Klaksvik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=klaksvik
    (108)  Kokopo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kokopo
    (109)  Mount Gambier:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mount+gambier
    (110)  Puerto Ayora:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=puerto+ayora
    (111)  Kodinsk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kodinsk
    (112)  Ossora:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ossora
    (113)  Colares:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=colares
    (114)  Maiduguri:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=maiduguri
    (115)  Saint-Francois:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint-francois
    (116)  Egvekinot:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=egvekinot
    (117)  Kaitangata:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kaitangata
    (118)  Cabo San Lucas:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cabo+san+lucas
    (119)  Burnie:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=burnie
    (120)  Bambanglipuro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bambanglipuro
    (121)  Kruisfontein:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kruisfontein
    (122)  Hilo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hilo
    (123)  Khirkiya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=khirkiya
    (124)  New Norfolk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=new+norfolk
    (125)  Mehamn:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mehamn
    (126)  Pedernales:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pedernales
    (127)  Estacion Coahuila:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=estacion+coahuila
    (128)  Saint-Philippe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint-philippe
    (129)  Mogadishu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mogadishu
    (130)  Kahului:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kahului
    (131)  Ozinki:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ozinki
    (132)  Kamyshevatskaya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kamyshevatskaya
    (133)  Padang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=padang
    (134)  Namibe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=namibe
    (135)  Natal:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=natal
    (136)  Moscow:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=moscow
    (137)  Necochea:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=necochea
    (138)  Bontang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bontang
    (139)  Karmala:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=karmala
    (140)  Dunedin:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=dunedin
    (141)  Bulalacao:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bulalacao
    (142)  Fort Nelson:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=fort+nelson
    (143)  Alofi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=alofi
    (144)  Manoel Urbano:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=manoel+urbano
    (145)  Ketchikan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ketchikan
    (146)  Rawatsar:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=rawatsar
    (147)  Bosaso:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bosaso
    (148)  Carnarvon:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=carnarvon
    (149)  Chokurdakh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chokurdakh
    (150)  Panama City:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=panama+city
    (151)  Chenzhou:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chenzhou
    (152)  Thaba Nchu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=thaba+nchu
    (153)  Qinhuangdao:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=qinhuangdao
    (154)  Sur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sur
    (155)  Atlantic Beach:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=atlantic+beach
    (156)  Joaima:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=joaima
    (157)  Mbigou:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mbigou
    (158)  Geraldton:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=geraldton
    (159)  Mahebourg:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mahebourg
    (160)  Cabedelo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cabedelo
    (161)  Tra Vinh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tra+vinh
    (162)  Arraial do Cabo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=arraial+do+cabo
    (163)  Payo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=payo
    (164)  Vilyuysk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vilyuysk
    (165)  Bud:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bud
    (166)  Norman Wells:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=norman+wells
    (167)  Eureka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=eureka
    (168)  Zhezkazgan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=zhezkazgan
    (169)  Sneek:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sneek
    (170)  Singaparna:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=singaparna
    (171)  Faribault:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=faribault
    (172)  Patacamaya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=patacamaya
    (173)  Avera:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=avera
    (174)  Thompson:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=thompson
    (175)  Urucara:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=urucara
    (176)  Bubaque:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bubaque
    (177)  Juegang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=juegang
    (178)  Muravlenko:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=muravlenko
    (179)  Lorengau:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lorengau
    (180)  Severo-Kurilsk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=severo-kurilsk
    (181)  Kropotkin:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kropotkin
    (182)  Margate:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=margate
    (183)  Lasa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lasa
    (184)  Victoria:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=victoria
    (185)  Meulaboh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=meulaboh
    (186)  Bereda:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bereda
    (187)  Safranbolu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=safranbolu
    (188)  Caravelas:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=caravelas
    (189)  San Cristobal:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=san+cristobal
    (190)  Slobidka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=slobidka
    (191)  Munirabad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=munirabad
    (192)  Aswan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=aswan
    (193)  Hasaki:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hasaki
    (194)  Batasan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=batasan
    (195)  Boa Vista:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=boa+vista
    (196)  Trinidad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=trinidad
    (197)  Saint George:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint+george
    (198)  Bambous Virieux:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bambous+virieux
    (199)  Ouro Fino:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ouro+fino
    (200)  Vila:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vila
    (201)  Mahibadhoo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mahibadhoo
    (202)  Kunming:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kunming
    (203)  Sumenep:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sumenep
    (204)  Isangel:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=isangel
    (205)  Coahuayana:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=coahuayana
    (206)  Putyatino:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=putyatino
    (207)  Ilulissat:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ilulissat
    (208)  Winneba:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=winneba
    (209)  Upernavik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=upernavik
    (210)  Tyukhtet:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tyukhtet
    (211)  Podgornoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=podgornoye
    (212)  Piopio:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=piopio
    (213)  Nara:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nara
    (214)  Gizo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gizo
    (215)  Ancud:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ancud
    (216)  Huarmey:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=huarmey
    (217)  Forestville:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=forestville
    (218)  Vrises:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vrises
    (219)  Tongren:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tongren
    (220)  Yelizovo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yelizovo
    (221)  Hithadhoo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hithadhoo
    (222)  Road Town:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=road+town
    (223)  North Platte:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=north+platte
    (224)  Agirish:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=agirish
    (225)  Tiruchchendur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tiruchchendur
    (226)  Vanimo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vanimo
    (227)  Thunder Bay:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=thunder+bay
    (228)  Aba:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=aba
    (229)  Kupang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kupang
    (230)  Sioux Lookout:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sioux+lookout
    (231)  Airai:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=airai
    (232)  Okhotsk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=okhotsk
    (233)  Tiksi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tiksi
    (234)  Preobrazheniye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=preobrazheniye
    (235)  Arica:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=arica
    (236)  Beira:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=beira
    (237)  Pevek:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pevek
    (238)  Kungurtug:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kungurtug
    (239)  Shieli:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=shieli
    (240)  La Romana:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=la+romana
    (241)  Mashhad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mashhad
    (242)  Kribi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kribi
    (243)  Port Hawkesbury:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=port+hawkesbury
    (244)  Guerrero Negro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=guerrero+negro
    (245)  Taguatinga:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=taguatinga
    (246)  Cockburn Town:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cockburn+town
    (247)  Natchitoches:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=natchitoches
    (248)  Ilam:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ilam
    (249)  Fortuna:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=fortuna
    (250)  Turukhansk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=turukhansk
    (251)  Gombe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gombe
    (252)  Luderitz:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=luderitz
    (253)  Peru:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=peru
    (254)  Portland:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=portland
    (255)  Terrace:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=terrace
    (256)  Iqaluit:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=iqaluit
    (257)  Baikunthpur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=baikunthpur
    (258)  Miram Shah:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=miram+shah
    (259)  Swan Hill:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=swan+hill
    (260)  Abeche:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=abeche
    (261)  Nyuksenitsa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nyuksenitsa
    (262)  Bustehrad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bustehrad
    (263)  Gannan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gannan
    (264)  Lerwick:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lerwick
    (265)  Port Macquarie:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=port+macquarie
    (266)  Nesna:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nesna
    (267)  Ibra:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ibra
    (268)  Laguna:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=laguna
    (269)  Sao Miguel do Iguacu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sao+miguel+do+iguacu
    (270)  Sapulpa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sapulpa
    (271)  Salinas:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=salinas
    (272)  Evensk:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=evensk
    (273)  Rorvik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=rorvik
    (274)  Sandy Bay:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sandy+bay
    (275)  Ankazoabo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ankazoabo
    (276)  Narwar:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=narwar
    (277)  Umm Kaddadah:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=umm+kaddadah
    (278)  Viedma:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=viedma
    (279)  Poya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=poya
    (280)  Polovinnoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=polovinnoye
    (281)  Kangaatsiaq:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kangaatsiaq
    (282)  Hambantota:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hambantota
    (283)  Houlton:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=houlton
    (284)  College:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=college
    (285)  Mikun:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mikun
    (286)  Mountain Home:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mountain+home
    (287)  Darhan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=darhan
    (288)  Kjollefjord:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kjollefjord
    (289)  Aksarka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=aksarka
    (290)  Paris:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=paris
    (291)  Sapa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sapa
    (292)  Ures:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ures
    (293)  Auray:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=auray
    (294)  Leningradskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=leningradskiy
    (295)  Palora:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=palora
    (296)  Tommot:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tommot
    (297)  Bang Saphan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bang+saphan
    (298)  Tungor:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tungor
    (299)  Vestmannaeyjar:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vestmannaeyjar
    (300)  Antalaha:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=antalaha
    (301)  Tasiilaq:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tasiilaq
    (302)  Meiganga:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=meiganga
    (303)  Teya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=teya
    (304)  Saint-Joseph:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint-joseph
    (305)  Nantucket:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nantucket
    (306)  Nikki:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nikki
    (307)  Lagoa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lagoa
    (308)  Atar:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=atar
    (309)  Bilma:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bilma
    (310)  Hualmay:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hualmay
    (311)  Tromso:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tromso
    (312)  Dormidontovka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=dormidontovka
    (313)  Decatur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=decatur
    (314)  Gigmoto:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gigmoto
    (315)  East London:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=east+london
    (316)  Kandrian:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kandrian
    (317)  Mgandu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mgandu
    (318)  Pandharpur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pandharpur
    (319)  Kaeo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kaeo
    (320)  Karratha:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=karratha
    (321)  Puerto Ayacucho:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=puerto+ayacucho
    (322)  Mitu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mitu
    (323)  Kysyl-Syr:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kysyl-syr
    (324)  Vao:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vao
    (325)  Alamos:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=alamos
    (326)  Pitimbu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pitimbu
    (327)  Rumford:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=rumford
    (328)  The Valley:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=the+valley
    (329)  Bressanone:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bressanone
    (330)  Oskemen:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=oskemen
    (331)  Benghazi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=benghazi
    (332)  Vygonichi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vygonichi
    (333)  Ambon:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ambon
    (334)  Waingapu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=waingapu
    (335)  San Patricio:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=san+patricio
    (336)  Marawi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=marawi
    (337)  Alice Springs:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=alice+springs
    (338)  Mudgee:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mudgee
    (339)  Igarka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=igarka
    (340)  Sola:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sola
    (341)  Mpongwe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mpongwe
    (342)  Vardo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vardo
    (343)  Aklavik:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=aklavik
    (344)  Pirovskoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pirovskoye
    (345)  Sandpoint:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sandpoint
    (346)  Anori:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=anori
    (347)  Goure:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=goure
    (348)  Faanui:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=faanui
    (349)  Hovd:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hovd
    (350)  Pervomayskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pervomayskiy
    (351)  Balad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=balad
    (352)  Ntungamo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ntungamo
    (353)  Yerofey Pavlovich:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yerofey+pavlovich
    (354)  Kvitok:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kvitok
    (355)  Tura:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tura
    (356)  Bathsheba:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bathsheba
    (357)  Kattivakkam:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kattivakkam
    (358)  Kodiak:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kodiak
    (359)  Wum:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=wum
    (360)  Yaan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yaan
    (361)  Sabang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sabang
    (362)  Kazachinskoye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kazachinskoye
    (363)  Pombia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=pombia
    (364)  Honningsvag:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=honningsvag
    (365)  Hofn:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hofn
    (366)  Kloulklubed:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kloulklubed
    (367)  Port Elizabeth:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=port+elizabeth
    (368)  Banfora:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=banfora
    (369)  Xining:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=xining
    (370)  Concordia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=concordia
    (371)  Mirabad:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mirabad
    (372)  Dalmatovo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=dalmatovo
    (373)  Terre-de-Bas:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=terre-de-bas
    (374)  Cap-aux-Meules:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cap-aux-meules
    (375)  Moron:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=moron
    (376)  Saint-Georges:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=saint-georges
    (377)  Ayorou:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ayorou
    (378)  Lukh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lukh
    (379)  Amalapuram:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=amalapuram
    (380)  Araouane:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=araouane
    (381)  Atencingo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=atencingo
    (382)  Esso:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=esso
    (383)  Bograd:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bograd
    (384)  Osoyoos:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=osoyoos
    (385)  Mackay:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mackay
    (386)  Eyl:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=eyl
    (387)  Varzelandia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=varzelandia
    (388)  Nome:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nome
    (389)  Yingcheng:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yingcheng
    (390)  Kavieng:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kavieng
    (391)  Maluanluan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=maluanluan
    (392)  Flinders:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=flinders
    (393)  Broken Hill:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=broken+hill
    (394)  Port Blair:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=port+blair
    (395)  Celestun:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=celestun
    (396)  Erzin:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=erzin
    (397)  Umea:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=umea
    (398)  Paamiut:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=paamiut
    (399)  Awbari:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=awbari
    (400)  Isa Khel:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=isa+khel
    (401)  Grua:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=grua
    (402)  Champerico:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=champerico
    (403)  Attingal:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=attingal
    (404)  Sambava:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sambava
    (405)  Zyryanka:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=zyryanka
    (406)  Yulara:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yulara
    (407)  Suntar:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=suntar
    (408)  Nemuro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=nemuro
    (409)  Urusha:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=urusha
    (410)  Shache:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=shache
    (411)  Palana:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=palana
    (412)  Fontem:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=fontem
    (413)  Tazovskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tazovskiy
    (414)  Sakleshpur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sakleshpur
    (415)  Bonthe:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bonthe
    (416)  Lodja:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lodja
    (417)  Ipswich:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ipswich
    (418)  Vagur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vagur
    (419)  Sao Joao da Barra:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sao+joao+da+barra
    (420)  Prince George:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=prince+george
    (421)  Souillac:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=souillac
    (422)  Tomari:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tomari
    (423)  Tabou:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tabou
    (424)  Carbonia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=carbonia
    (425)  Chumikan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=chumikan
    (426)  Amahai:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=amahai
    (427)  Clyde River:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=clyde+river
    (428)  Flin Flon:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=flin+flon
    (429)  San Juan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=san+juan
    (430)  Salalah:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=salalah
    (431)  Buchanan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=buchanan
    (432)  Show Low:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=show+low
    (433)  Khandyga:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=khandyga
    (434)  Severo-Yeniseyskiy:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=severo-yeniseyskiy
    (435)  Constitucion:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=constitucion
    (436)  Vredendal:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=vredendal
    (437)  Zhanaozen:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=zhanaozen
    (438)  Caltagirone:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=caltagirone
    (439)  Mahon:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mahon
    (440)  Santiago del Estero:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=santiago+del+estero
    (441)  Moyale:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=moyale
    (442)  Manicore:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=manicore
    (443)  Linjiang:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=linjiang
    (444)  Uberlandia:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=uberlandia
    (445)  Broome:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=broome
    (446)  Samarai:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=samarai
    (447)  Hamilton:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=hamilton
    (448)  Coquimbo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=coquimbo
    (449)  Buta:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=buta
    (450)  Namatanai:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=namatanai
    (451)  Kitgum:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kitgum
    (452)  Kissamos:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kissamos
    (453)  Shingu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=shingu
    (454)  Formosa:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=formosa
    (455)  Qingdao:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=qingdao
    (456)  Trindade:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=trindade
    (457)  Yokaichi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=yokaichi
    (458)  Zastron:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=zastron
    (459)  Kramat:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kramat
    (460)  Mirzapur:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mirzapur
    (461)  Moerai:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=moerai
    (462)  Abu Dhabi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=abu+dhabi
    (463)  Noumea:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=noumea
    (464)  Katobu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=katobu
    (465)  Batagay-Alyta:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=batagay-alyta
    (466)  Fethiye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=fethiye
    (467)  Lebyazhye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lebyazhye
    (468)  Ulundi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ulundi
    (469)  Qaqortoq:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=qaqortoq
    (470)  Touros:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=touros
    (471)  San Angelo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=san+angelo
    (472)  Akom:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=akom
    (473)  Quatre Cocos:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=quatre+cocos
    (474)  Grimshaw:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=grimshaw
    (475)  Kyabram:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kyabram
    (476)  Mount Pleasant:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mount+pleasant
    (477)  High Level:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=high+level
    (478)  Mvangue:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mvangue
    (479)  Tezu:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=tezu
    (480)  Ekhabi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ekhabi
    (481)  San Pedro:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=san+pedro
    (482)  Santa Cruz:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=santa+cruz
    (483)  Kurumkan:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kurumkan
    (484)  Boddam:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=boddam
    (485)  Sarkand:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sarkand
    (486)  Bandarbeyla:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bandarbeyla
    (487)  Phan Thiet:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=phan+thiet
    (488)  Mabaruma:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=mabaruma
    (489)  Iquique:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=iquique
    (490)  Gaurnadi:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=gaurnadi
    (491)  Oussouye:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=oussouye
    (492)  Bridlington:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=bridlington
    (493)  Sorland:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=sorland
    (494)  Lavrentiya:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=lavrentiya
    (495)  Cidreira:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=cidreira
    (496)  Horsham:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=horsham
    (497)  Praia da Vitoria:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=praia+da+vitoria
    (498)  Kudahuvadhoo:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=kudahuvadhoo
    (499)  Ahipara:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=ahipara
    (500)  Utamysh:  http://api.openweathermap.org/data/2.5/weather?appid=40d439259718ef3f486d5ccb188390f5&units=imperial&q=utamysh
    


```python
#extract fields to dataframe, save to .csv

header = ['City']
weatherdata = pd.DataFrame([data.get("name") for data in city_data], columns=header)
weatherdata['Latitude'] = pd.DataFrame([data.get("coord").get("lat") for data in city_data])
weatherdata['Temperature'] = pd.DataFrame([data.get("main").get("temp") for data in city_data])
weatherdata['Humidity'] = pd.DataFrame([data.get("main").get("humidity") for data in city_data])
weatherdata['Cloudiness'] = pd.DataFrame([data.get("clouds").get("all") for data in city_data])
weatherdata['Wind_Speed'] = pd.DataFrame([data.get("wind").get("speed") for data in city_data])
weatherdata.to_csv("weatherdata.csv", encoding='utf-8', index=False)
```


```python
#Temperature (F) vs. Latitude

plt.figure(figsize=(10,6))
plt.style.use('seaborn')
plt.title("City Latitude vs. Temperature\nUpdated: "+ (time.strftime("%m/%d/%Y")))
plt.xlabel("Latitude")
plt.ylabel("Max Temperature (F)")
plt.scatter(weatherdata["Latitude"], weatherdata["Temperature"], alpha=.55,
            c="c", edgecolors="black", linewidth=1)
plt.savefig('temperature.png')
plt.show()
```


![png](output_3_0.png)



```python
#Humidity (%) vs. Latitude

plt.figure(figsize=(10,6))
plt.style.use('seaborn')
plt.title("City Latitude vs. Humidity\nUpdated: "+ (time.strftime("%m/%d/%Y")))
plt.xlabel("Latitude")
plt.ylabel("Humidity (%)")
plt.scatter(weatherdata["Latitude"], weatherdata["Humidity"], alpha=.55,
            c="c", edgecolors="black", linewidth=1)
plt.savefig('humidity.png')
plt.show()
```


![png](output_4_0.png)



```python
#Cloudiness (%) vs. Latitude

plt.figure(figsize=(10,6))
plt.style.use('seaborn')
plt.title("City Latitude vs. Cloudiness\nUpdated: "+ (time.strftime("%m/%d/%Y")))
plt.xlabel("Latitude")
plt.ylabel("Cloudiness (%)")
plt.scatter(weatherdata["Latitude"], weatherdata["Cloudiness"], alpha=.55,
            c="c", edgecolors="black", linewidth=1)
plt.savefig('cloudiness.png')
plt.show()
```


![png](output_5_0.png)



```python
#Wind Speed (mph) vs. Latitude

plt.figure(figsize=(10,6))
plt.style.use('seaborn')
plt.title("City Latitude vs. Wind Speed\nUpdated: "+ (time.strftime("%m/%d/%Y")))
plt.xlabel("Latitude")
plt.ylabel("Wind Speed (MPH)")
plt.scatter(weatherdata["Latitude"], weatherdata["Wind_Speed"], alpha=.55,
            c="c", edgecolors="black", linewidth=1)
plt.savefig('wind.png')
plt.show()
```


![png](output_6_0.png)

