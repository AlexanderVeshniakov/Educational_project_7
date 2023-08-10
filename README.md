### Цели
Американское туристическое агентство хочет разрекламировать свои услуги при помощи установки банеров. 
Требуется найти наилучшие точки установки. 
Эти банеры должны покрывать наиболее популярные заведения, а также быть недалеко от самих офисов агентства.

### 1
Загружаем данные о посещениях заведений: 
- checkins.dat: отмечает чекины (посещения) пользователей на площадках. Каждая регистрация имеет уникальный             идентификатор,              а       также идентификатор пользователя и идентификатор места проведения.
- Очищаем данные от записей с пропусками. 
- Выводим количество записей после очистки

### 2
С помощью геолокаций и библиотеки [Reverse Geocoder](https://github.com/thampiman/reverse-geocoder),
узнай страну для каждой геопозиции.
Выводим **название** второй страны по количеству записей.

### 3
Так как нас интересуют только Американские локации:
- Очищаем данные от локации других стран
- Оставляем 50 самых часто встречаемых заведений (venue_id).
- Выводим количество локаций, оставшихся после этих очисток.

### 4
Решаем задачу кластеризации. 
- Пользуемся алгоритмом [Mean Shift] для кластеризации локаций. 
- В параметрах указываем `MeanShift(bandwidth=0.1, bin_seeding=True)`:
    - `bandwidth=0.1` - это ширина ядра кластеризации. Для средних широт США - это порядка 5-10 км. 
    - `bin_seeding=True` - для ускорения работы алгоритма.
    
Выводим количество кластеров.

### 5
Находим те центры кластеров, которые наиболее близко находятся к офисам продаж компании.
Загружаем [данные по координатам офисов компании](datasets/offices.csv). Для каждого офиса найди 5 самых ближайших к нему центров кластеров. 
(Пренебрежем тем, что Земля круглая и рассчитаем Евклидово расстояние).
У компании 11 офисов, значит у нас должно получится 55 мест установки баннеров. 
Выведем координаты установки баннера, который ближе всего находится к офису компании.

### 6
Отображаем точки расположения баннеров
_________________________________________________________________________________________________________________________

### Goals
The American travel agency wants to advertise its services by installing banners.
You need to find the best installation points.
These banners should cover the most popular establishments, as well as be close to the agency's offices themselves.

### 1
We upload data on visits to institutions:
- checkins.dat: marks the checks (visits) of users at the sites. Each registration has a unique identifier, as well as a user ID and venue ID.
- We clear the data from records with omissions.
- Output the number of records after cleaning

### 2
Using geolocation and the [Reverse Geocoder] library (https://github.com/thampiman/reverse-geocoder),
recognize the country for each geoposition.
We display ** the name ** of the second country by the number of records.

### 3
Since we are only interested in American locations:
- We clear the data from the location of other countries
- Leave the 50 most frequently encountered establishments (venue_id).
- We display the number of locations remaining after these cleanups.

### 4
We solve the clustering problem.
- We use the [Mean Shift] algorithm to cluster locations.
- In the parameters, specify 'MeanShift (bandwidth = 0.1, bin_seeding=True)':
- 'bandwidth = 0.1' is the width of the clustering core. For middle latitudes, the United States is about 5-10 km.
- 'bin _ seeding = True' - to speed up the algorithm.

Output the number of clusters.

### 5
We find those cluster centers that are closest to the company's sales offices.
We load [data on the coordinates of company offices] (datasets/offices.csv). For each office, find the 5 closest cluster centers to it.
(Let's neglect that the Earth is round and calculate the Euclidean distance).
The company has 11 offices, which means we should have 55 places to install banners.
Let's display the coordinates of the banner installation, which is closest to the company's office.

### 6
Display banner location points