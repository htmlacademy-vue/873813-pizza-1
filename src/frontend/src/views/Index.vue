<template>
  <!DOCTYPE html>
  <html lang="ru">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1" />
      <title>V!U!E! Pizza - главная</title>
    </head>
    <body>
      <header class="header">
        <div class="header__logo">
          <a href="index.html" class="logo">
            <img
              src="@/assets/img/logo.svg"
              alt="V!U!E! Pizza logo"
              width="90"
              height="40"
            />
          </a>
        </div>
        <div class="header__cart">
          <a href="cart.html">0 ₽</a>
        </div>
        <div class="header__user">
          <a href="#" class="header__login"><span>Войти</span></a>
        </div>
      </header>
      <main class="content">
        <form action="#" method="post">
          <div class="content__wrapper">
            <h1 class="title title--big">Конструктор пиццы</h1>

            <div class="content__dough">
              <div class="sheet">
                <h2 class="title title--small sheet__title">Выберите тесто</h2>

                <div class="sheet__content dough">
                  <label
                    v-for="item in dough"
                    :key="item.id"
                    :class="`dough__input dough__input--${getDough(item.id)}`"
                  >
                    <input
                      type="radio"
                      name="dought"
                      :value="getDough(item.id)"
                      class="visually-hidden"
                    />
                    <b>{{ item.name }}</b>
                    <span>{{ item.description }}</span>
                  </label>
                </div>
              </div>
            </div>

            <div class="content__diameter">
              <div class="sheet">
                <h2 class="title title--small sheet__title">Выберите размер</h2>

                <div class="sheet__content diameter">
                  <label
                    v-for="size in sizes"
                    :key="size.id"
                    :class="`diameter__input diameter__input--${getSize(
                      size.id
                    )}`"
                  >
                    <input
                      type="radio"
                      name="diameter"
                      :value="getSize(size.id)"
                      class="visually-hidden"
                    />
                    <span>{{ size.name }}</span>
                  </label>
                </div>
              </div>
            </div>

            <div class="content__ingredients">
              <div class="sheet">
                <h2 class="title title--small sheet__title">
                  Выберите ингредиенты
                </h2>

                <div class="sheet__content ingredients">
                  <div class="ingredients__sauce">
                    <p>Основной соус:</p>

                    <label
                      v-for="sauce in sauces"
                      :key="sauce.id"
                      class="radio ingredients__input"
                    >
                      <input
                        type="radio"
                        name="sauce"
                        :value="getSauce(sauce.id)"
                      />
                      <span>{{ sauce.name }}</span>
                    </label>
                  </div>

                  <div class="ingredients__filling">
                    <p>Начинка:</p>

                    <ul class="ingredients__list">
                      <li
                        v-for="ingredient in ingredients"
                        :key="ingredient.id"
                        class="ingredients__item"
                      >
                        <span
                          :class="`filling filling--${getIngredient(
                            ingredient.id
                          )}`"
                          >{{ ingredient.name }}</span
                        >

                        <div
                          class="counter counter--orange ingredients__counter"
                        >
                          <button
                            type="button"
                            class="counter__button counter__button--minus"
                            disabled
                          >
                            <span class="visually-hidden">Меньше</span>
                          </button>
                          <input
                            type="text"
                            name="counter"
                            class="counter__input"
                            value="0"
                          />
                          <button
                            type="button"
                            class="counter__button counter__button--plus"
                          >
                            <span class="visually-hidden">Больше</span>
                          </button>
                        </div>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>

            <div class="content__pizza">
              <label class="input">
                <span class="visually-hidden">Название пиццы</span>
                <input
                  type="text"
                  name="pizza_name"
                  placeholder="Введите название пиццы"
                />
              </label>

              <div class="content__constructor">
                <div class="pizza pizza--foundation--big-tomato">
                  <div class="pizza__wrapper">
                    <div class="pizza__filling pizza__filling--ananas"></div>
                    <div class="pizza__filling pizza__filling--bacon"></div>
                    <div class="pizza__filling pizza__filling--cheddar"></div>
                  </div>
                </div>
              </div>

              <div class="content__result">
                <p>Итого: 0 ₽</p>
                <button type="button" class="button" disabled>Готовьте!</button>
              </div>
            </div>
          </div>
        </form>
      </main>
    </body>
  </html>
</template>

<script>
import misc from "@/static/misc.json";
import pizza from "@/static/pizza.json";
import user from "@/static/user.json";
import additionalData from "@/static/additionalData.json";

export default {
  name: "Index",
  data: function () {
    return {
      test: "Test phrase",
      misc,
      user,
      sizes: pizza.sizes,
      sauces: pizza.sauces,
      ingredients: pizza.ingredients,
      dough: pizza.dough,
      additionalData,
    };
  },
  methods: {
    getSize(id) {
      return additionalData.sizes[id];
    },
    getIngredient(id) {
      return additionalData.ingredients[id];
    },
    getDough(id) {
      return additionalData.dough[id];
    },
    getSauce(id) {
      return additionalData.sauces[id];
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~@/assets/scss/app.scss";
</style>
