---
layout: post
title:  "Первый опыт: сортировка объектов и массивов"
date:   2023-04-26 18:40:18 +0300
categories: js/react
---

Вывел на странице `Button.stories.mdx` в Storybook (под React) все варианты кнопок, использованных в дизайн-макете. Решил их упорядочить по ширине. Для этого написал функцию сортировки исходного объекта. 

Возникли сложности с типами данных, их обработкой и рендерингом результата. Первые 2 вопроса решил. По сути, написал `говнокод`. Алгоритмы не применял. В эту тему нужно погружаться контретно. Это интересная и полезная тема.

------  

Вот, что мне удалось сочинить, пользуясь подсказками из интернета и собственной логикой. 

На входе есть объект с переменными, упорядоченный по их именам. 
На выходе требуется получить объект с названиями этих же переменных, упорядоченных по их свойству -- по размеру кнопок.

**Важно:** 
- изначально в `css-файле` заданы переменные, которые переводят числовые значения в пикселях в сроковые значения. В пропсах компонентов используются именно строковы названия: `exsra-small`, `large` и т.п.
- код обернул в единую функцию, чтобы его можно было экспортировать в другие файлы проекта. Возможно, здесь классовый подход был бы лучше. Надо подумать;
- переменные отличаются названием (ключами) и значениями. Переменные заданы в `Button.stories.js` вот в таком виде:

```js
export const signUpButton1 = {
  args: {
    label: 'Записаться на экскурсию',
    buttonType: 'button',
    buttonSize: 'extra-small', // именно это значение мне нужно для сортировки!!!
    backgroundColor: '#8081BD',
    fontColor: '#FFF',
    fontWeight: '700',
    fontSize: '12px',
    lineHeight: '15px',
    isUppercase: false,
    border: false,
    onClick: undefined
  }
};
```

Ну, и сам **код функции**:
```jsx
export const renderButtonsBySize = (Story, ButtonStories) => {

// изначальный объект с данными (переменные);
  const buttonsObj = {
    signUpButton1, signUpButton2, signUpButton3, signUpButton4, signUpButton5, signUpButton6
  };

// создаем новый объект с теми же ключами, а из всех свойств вытаскиваем только нужные (ширину кнопки);
  const makeNewButtonObj = () => {
    const newButtonsObj = {};

    for (let key in buttonsObj) {
    newButtonsObj[key] = buttonsObj[key]['args']['buttonSize'];
  };

    return newButtonsObj;
  };

// формируем массив значений. Т.е. нужно понять, какие вообще есть значения ширины кнопок. Это послужит эталоном для сравнения.
  const createSizesArr = () => {
    const sizesArr = Object.values(makeNewButtonObj());
    let sortedSizesArr = sizesArr.filter((element, index, self) => {
      return index === self.indexOf(element);
    });

    return sortedSizesArr;
  };

// 1. перебираем объект с кнопками и сравниваем их ширину с эталоном.
// 2. тем самым создаем новый массив ну нужной последовательности - по ширине кнопки. При этом сохраняем названия ключей. Именно они нам важны, чтобы конкатенировать их.

  const sortButtonsBySize = () => {
    const newButtonsObj = makeNewButtonObj();
    const sortedSizesArr = createSizesArr();

    const sortedButtonsArr = [];

    for (let size in sortedSizesArr) {
      for (let element in newButtonsObj) {
        if (sortedSizesArr[size] === newButtonsObj[element]) {
          sortedButtonsArr.push(element);
        };
      };
    };

    return sortedButtonsArr;
  };

  const arr = sortButtonsBySize();

```