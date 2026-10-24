# Лабораторная работа 4. Разработка с использованием frontend-фреймворков

## Задача
Сделать SPA на React или Vue с данными из API:
- Список с поиском и пагинацией
- Детальный просмотр элемента в модальном окне или боковой панели — есть разные смысловые блоки
- Создание, редактирование и удаление элементов
- Фильтрация

Проект в том же репозитории в **отдельной** ветке (например, `lab-4`)

## Источник данных

**Общие требования**: наличие пагинации, изображений, даты создания объектов, богатая доменная модель (существует больше одной сущности)

На выбор:

- [Star Wars API](https://www.swapi.tech/)
- [Mock Products API](https://dummyjson.com/docs/products)
- [Pokemon API](https://pokeapi.co/)
- [Anime API](https://docs.api.jikan.moe/)
- своё моковое API на [MSW](https://mswjs.io). Если создаете моки, то должен быть полноценный CRUD

## Стек технологий

**База:** React 19 или Vue 3, Vite, TypeScript

**Стилизация [на выбор]**: CSS Modules, Tailwind, styled-components, emotion, SCSS и т.п. **При выборе подхода надо суметь объяснить выбор: назвать плюсы и минусы**

Интерфейс собирается через **библиотеку компонентов [тоже на выбор]**:

- React: [Mantine](https://mantine.dev/), [Material UI](https://mui.com/), [Chakra UI](https://chakra-ui.com/), [Hero UI](https://heroui.com/)
- Vue: [Vuetify](https://vuetifyjs.com/), [PrimeVue](https://primevue.org/), [Naive UI](https://www.naiveui.com/), [Element Plus](https://element-plus.org/)
- Angular: [Material](https://material.angular.dev), [PrimeNG](https://primeng.org), [Spartan](https://spartan.ng), [Taiga UI](https://taiga-ui.dev)

Глобальной разницы между ними нет, берите что понравилось больше. Можно брать любой другой ui-kit — главное, чтобы в нем было много разных компонентов.

## Требования к реализации

- React — **только** функциональные компоненты; Vue — Composition API (`<script setup>`)
- Поиск с `debounce`: запрос не уходит на каждое нажатие клавиши
- Запросы вынесены в отдельный модуль, компоненты не вызывают `fetch` напрямую
- У каждого списка есть четыре состояния:
  1. Загрузка. Нужен компонент `skeleton`
  2. Ошибка с кнопкой повтора
  3. Пустой результат
  4. Отображение самих данных
- Удаление с подтверждением в модальном окне
- После создания, правки и удаления интерфейс обновляется без перезагрузки страницы, результат операции показывается уведомлением — можно
  воспользоваться библиотекой [Sonner](https://github.com/emilkowalski/sonner) (для Vue — [vue-sonner](https://github.com/xiaoluoboding/vue-sonner)), либо решением из вашего ui-kit
- `key` в списках — id сущности, не индекс;
- отфильтрованные и вычисляемые данные не хранятся в отдельном состоянии, а считаются при рендере (во Vue — через `computed`);
- **интерфейс адаптивный**

## Запрещено

1. Классовые компоненты в React, Options API во Vue
2. Работа с DOM через `document.querySelector` и аналоги
3. TanStack Query, SWR, RTK Query, Pinia Colada, `useFetch` из VueUse и другие библиотеки для серверного состояния
