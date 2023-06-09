# Проект «Жёлтая резиновая уточка»

## 1. Описание

Жёлтая резиновая уточка, высотой 3 см.

Может плавать, летает (если ей не связали крылья) и крякает по команде заданное
количество раз с заданной периодичностью.

## 2. Требования к реализации

### 2.1. Данные о сервисе

#### Сервис
yellow-rubber-duck

#### URL
+ http://localhost:2222
+ http://localhost:2222/swagger-ui.html

#### JAR
+ [yellow-rubber-duck-0.0.1.jar](application/yellow-rubber-duck-0.0.1.jar)
+ [yellow-rubber-duck-0.0.2.jar](application/yellow-rubber-duck-0.0.2.jar)

#### Запуск
```bash
java -jar yellow-rubber-duck-0.0.1.jar
java -jar yellow-rubber-duck-0.0.2.jar
```

### 2.2. Характеристики объекта

| Характеристика    | Поле         | Значение          |
|:------------------|:-------------|:------------------|
| Цвет              | color        | yellow            |
| Материал          | material     | rubber            |
| Размер            | metersHeight | 0,03              |
| Звук              | sound        | quack             |
| Состояние крыльев | wingsState   | { ACTIVE, FIXED } |

### 2.3. Методы

#### 2.3.1. Метод `properties`

Метод позволяет получить характеристики Жёлтой резиновой уточки.

##### Тип запроса
POST

##### API
`/api/duck/properties`

| Параметры                                       | Результат                                                                                                         |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| **Body:** { “material”: “rubber” }              | **HTTP status code:** 200 OK<br>**Body:** { “color”: “yellow”,<br>“material”: “rubber”,<br>“metersHeight”: 0.03 } |
| **Body:** { “material”: Любое другое значение } | **HTTP status code:** 200 OK<br>**Body:** {}                                                                      |

#### 2.3.2. Метод `fly`

Метод позволяет Жёлтой резиновой уточке лететь или отказаться от полёта.

##### Тип запроса
GET 

##### API
`/api/duck/fly` 

| Параметры              | Результат                                                             |
|:-----------------------|:----------------------------------------------------------------------|
| URL:?wingsState=ACTIVE | **HTTP status code:** 200 OK<br>**Body:** { “message”: “I’m flying” } |
| URL:?wingsState=FIXED  | **HTTP status code:** 200 OK<br>Body: { “message”: “I can’t fly” }    |

#### 2.3.3. Метод `swim`

Метод позволяет Жёлтой резиновой уточке плыть.

##### Тип запроса
GET 

##### API
`/api/duck/swim`

| Параметры | Результат                                                               |
|:----------|:------------------------------------------------------------------------|
| нет       | **HTTP status code:** 200 OK<br>**Body:** { “message”: “I’m swimming” } |

#### 2.3.4. Метод `sound`

Метод позволяет Жёлтой резиновой уточке крякать.

##### Тип запроса
POST

##### API
`/api/duck/sound`

##### Параметры метода

Параметрами являются количество повторений (repetitionCount), количество «кряков» в звуке (soundCount).
Параметры передаются в URL.

Особенности:
+ Количество повторений - целое число >= 0 
+ Количество «кряков» в звуке - целое число >= 0

**Возвращаемый результат**

Например, количество повторений = 3, количество «кряков» в звуке = 2:
```
HTTP status code: 200 OK
Body:
{ “sound”: “quack-quack, quack-quack, quack-quack” }
```

Особенности:
+ Если количество «кряков» == 0 или количество повторений == 0, то 
```
HTTP status code: 200 OK
Body: { “sound”: “” }
```


