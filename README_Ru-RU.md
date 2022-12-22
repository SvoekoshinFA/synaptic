

Synaptic [![Статус сборки](https://travis-ci.org/cazala/synaptic.svg?branch=master)](https://travis-ci.org/cazala/synaptic) [![Присоединиться к чату на https://synapticjs.slack.com](https://synaptic-slack.now.sh/badge.svg)](https://synaptic-slack.now.sh/)
========

## Важно: [Synaptic 2.x](https://github.com/cazala/synaptic/issues/140) сейчас находится в стадии обсуждения! Не стесняйтесь участвовать

Synaptic — это библиотека нейронной сети javascript для **node.js** и **браузера**, ее обобщенный алгоритм не зависит от архитектуры, поэтому вы можете создавать и обучать практически любой тип нейронной сети первого порядка или даже [нейронную сеть второго порядка]. ](http://en.wikipedia.org/wiki/Recurrent_neural_network#Second_Order_Recurrent_Neural_Network).

Эта библиотека включает в себя несколько встроенных архитектур, таких как [многослойные перцептроны](http://en.wikipedia.org/wiki/Multilayer_perceptron), [многослойная долговременная память](http://en.wikipedia.org/wiki /Long_short_term_memory) сети (LSTM), [жидкостные машины](http://en.wikipedia.org/wiki/Liquid_state_machine) или [Hopfield](http://en.wikipedia.org/wiki/Hopfield_network) и тренер, способный обучать любую заданную сеть, который включает в себя встроенные обучающие задачи/тесты, такие как решение XOR, выполнение задачи вызова отвлеченной последовательности или [встроенная грамматика Ребера] (http://www.willamette.edu/~gorr/ classs/cs449/reber.html), поэтому вы можете легко протестировать и сравнить производительность различных архитектур.


Алгоритм, реализованный этой библиотекой, был взят из статьи Дерека Д. Моннера:

[Обобщенный алгоритм обучения, подобный LSTM, для рекуррентных нейронных сетей второго порядка] (http://www.overcomplete.net/papers/nn2012.pdf)


В этой статье есть ссылки на уравнения, прокомментированные в исходном коде.

#### Вступление

Если у вас нет предварительных знаний о нейронных сетях, вам следует начать с [чтения этого руководства] (https://github.com/cazala/synaptic/wiki/Neural-Networks-101).


Если вам нужен практический пример того, как передавать данные в нейронную сеть, взгляните на [эту статью] (https://github.com/cazala/synaptic/wiki/Normalization-101).

Вы также можете ознакомиться с [этой статьей] (http://blog.webkid.io/neural-networks-in-javascript/).

#### Демо

- [Решить XOR](http://caza.la/synaptic/#/xor)
- [Задача вызова дискретной последовательности] (http://caza.la/synaptic/#/dsr)
- [Изучите фильтры изображений] (http://caza.la/synaptic/#/image-filters)
- [Нарисуй изображение](http://caza.la/synaptic/#/paint-an-image)
- [Карта самоорганизации] (http://caza.la/synaptic/#/self-organizing-map)
- [Читать из Википедии](http://caza.la/synaptic/#/wikipedia)
- [Создание простой нейронной сети (видео)] (https://scrimba.com/casts/cast-1980)
- [Научитесь стрелять](https://sta-ger.bitbucket.io/apps/bot/index.html)
- [Классификатор пивных бокалов](https://sta-ger.bitbucket.io/apps/beer/index.html)

Исходный код этих демонстраций можно найти в [этой ветке](https://github.com/cazala/synaptic/tree/gh-pages/scripts).

#### Начиная

- [Нейроны] (https://github.com/cazala/synaptic/wiki/Neurons/)
- [Слои] (https://github.com/cazala/synaptic/wiki/Слои/)
- [Сети] (https://github.com/cazala/synaptic/wiki/Networks/)
- [Тренер](https://github.com/cazala/synaptic/wiki/Trainer/)
- [Архитектор] (https://github.com/cazala/synaptic/wiki/Architect/)

Чтобы опробовать примеры, ознакомьтесь с веткой [gh-pages](https://github.com/cazala/synaptic/tree/gh-pages).

`git checkout gh-pages`

#### Другие языки

Этот README также доступен на других языках.

- [китайский упрощенный | 中文文档](https://github.com/cazala/synaptic/blob/master/README_Zh-CN.md), благодаря [@noraincode](https://github.com/noraincode).
- [Традиционный китайский | 繁體中文](https://github.com/cazala/synaptic/blob/master/README_Zh-TW.md), автор [@NoobTW](https://github.com/noobtw).
- [Японский | 日本語] (https://github.com/cazala/synaptic/blob/master/README_Ja-JP.md), спасибо [@oshirogo] (https://github.com/dscripps).

## Обзор

### Установка

##### В узле

Вы можете установить synaptic с помощью [npm](http://npmjs.org):

``команда
npm установить синаптик --save
```

##### В браузере

Вы можете установить synaptic с помощью [bower](http://bower.io):

``команда
беседка установить синаптик
```

Или вы можете просто использовать ссылку CDN, любезно предоставленную [CDNjs] (https://cdnjs.com/)

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/synaptic/1.1.4/synaptic.js"></script>
```

### Применение

```javascript
var synaptic = require('synaptic'); // эта строка не нужна в браузере
var Нейрон = синаптический.Нейрон,
Слой = синаптический. Слой,
Сеть = synaptic.Network,
Тренер = synaptic.Trainer,
Архитектор = synaptic.Architect;
```

Теперь вы можете начать создавать сети, обучать их или использовать встроенные сети из [Architect](https://github.com/cazala/synaptic/wiki/Architect/).

### Примеры

##### Персептрон

Вот как вы можете создать простой **персептрон**:

![персептрон](http://www.codeproject.com/KB/dotnet/predictor/network.jpg).

```javascript
функция Perceptron(вход, скрытый, выход)
{
// создаем слои
var inputLayer = новый слой (вход);
var hiddenLayer = новый слой (скрытый);
var outputLayer = новый слой (выход);

// соединяем слои
inputLayer.project (скрытый слой);
скрытыйслой.проект (выходной слой);

// устанавливаем слои
this.set({
ввод: входной слой,
скрытый: [скрытый слой],
вывод: выходной слой
});
}

// расширяем цепочку прототипов
Perceptron.prototype = новая сеть();
Персептрон.прототип.конструктор = Персептрон;
```

Теперь вы можете протестировать свою новую сеть, создав тренер и научив персептрон изучать XOR.

```javascript
var myPerceptron = новый перцептрон (2,3,1);
var myTrainer = новый тренер (myPerceptron);

myTrainer.XOR(); // { ошибка: 0.004998819355993572, итераций: 21871, время: 356 }

myPerceptron.activate([0,0]); // 0,0268581547421616
myPerceptron.activate([1,0]); // 0,9829673642853368
myPerceptron.activate([0,1]); // 0,9831714267395621
myPerceptron.activate([1,1]); // 0,02128894618097928
```

##### Долгая кратковременная память

Вот как вы можете создать простую сеть **долгой кратковременной памяти** с входными воротами, воротами забывания, выходными воротами и глазками:

![долгая кратковременная память](http://people.idsia.ch/~juergen/lstmcell4.jpg)

```javascript
функция LSTM(ввод, блоки, вывод)
{
// создаем слои
var inputLayer = новый слой (вход);
var inputGate = новый слой (блоки);
var забылGate = новый слой (блоки);
var memoryCell = новый слой (блоки);
var outputGate = новый слой (блоки);
var outputLayer = новый слой (выход);

// соединения из входного слоя
var input = inputLayer.project(memoryCell);
inputLayer.project(inputGate);
inputLayer.project(forgetGate);
inputLayer.project(outputGate);

// соединения из ячейки памяти
var output = memoryCell.project(outputLayer);

// самоподключение
var self = memoryCell.project(memoryCell);

// глазки
memoryCell.project(inputGate);
memoryCell.project(forgetGate);
memoryCell.project(outputGate);

// ворота
inputGate.gate(вход, Layer.gateType.INPUT);
забудьтеGate.gate(я, Layer.gateType.ONE_TO_ONE);
outputGate.gate(выход, Layer.gateType.OUTPUT);

// прямое соединение ввода-вывода
входной слой.проект (выходной слой);

// устанавливаем слои нейронной сети
this.set({
ввод: входной слой,
скрыто: [inputGate, ForgetGate, memoryCell, outputGate],
вывод: выходной слой
});
}

// расширяем цепочку прототипов
LSTM.prototype = новая сеть();
LSTM.prototype.constructor = LSTM;
```

Это примеры для пояснительных целей, [Architect] (https://github.com/cazala/synaptic/wiki/Architect/) уже включает многослойные персептроны и
Многоуровневые сетевые архитектуры LSTM.

## Делать вклад

**Synaptic** — это проект с открытым исходным кодом, начатый в Буэнос-Айресе, Аргентина. Любой человек со всего мира может внести свой вклад в развитие проекта.

Если вы хотите внести свой вклад, не стесняйтесь присылать PR, просто обязательно запустите **npm run test** и **npm run build** перед отправкой. Таким образом вы запустите все тестовые спецификации и соберете файлы веб-дистрибутива.

## Поддерживать

Если вам нравится этот проект и вы хотите выразить свою поддержку, вы можете купить мне пиво за [волшебные интернет-деньги](https://i.imgur.com/mScSiOo.jpg):

```
Биткойн: 16ePagGBbHfm2d6esjMXcUBTNgqpnLWNeK
Эфириум: 0xa423bfe9db2dc125dd3b56f215e09658491cc556
LTC: LeeemeZj6YL6pkTTtEGHFD6idDxHBF2HXa
XMR: 46WNbmwXpYxiBpkbHjAgjC65cyzAxtaaBQjcGpAZquhBKw2r8NtPQniEgMJcwFMCZzSBrEJtmPsTR54MoGBDbjTi2W1XmgM
```

<3