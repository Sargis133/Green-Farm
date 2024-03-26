<template>
  <div class="main-page">
    <div id="header" class="main-page__header-content">
      <img
        src="/images/main/header_cont_l.png"
        class="header-left-cont"
        alt="img"
      />
      <div class="header-content__items-box">
        <div class="items-box__logo-aside">
          <ui-icons name="logo" />
        </div>
        <div class="items-box__nav-box">
          <div class="nav-box__message-aside">
            <div class="message-aside__icon">
              <ui-icons name="message" />
            </div>
            <div class="message-aside__email-box">
              <div class="email-box__text">
                <NuxtLink to="/">info@floratrans.ru</NuxtLink>
              </div>
              <div class="email-box__send-message">
                <NuxtLink to="/">Написать письмо</NuxtLink>
              </div>
            </div>
          </div>

          <div class="items-box__number-aside">
            <ui-icons name="whatsapp" />
            <NuxtLink to="/"> +7 977 909 97 60 </NuxtLink>
          </div>
          <div class="items-box__send-whatsapp-aside">
            <button class="send-whatsapp-aside__button">
              Написать WhatsApp
            </button>
          </div>
        </div>
        <div class="items-box__burger-menu">
          <div class="burger-menu__icon-box" @click="onOpenMenuFunc">
            <ui-icons name="menu" />
          </div>
          <div v-if="isShowBurgerMenu" class="burger-menu__items-box">
            <button
              class="burger-menu__close-button"
              @click="onCloseBurgerMenu"
            >
              <ui-icons name="close" />
            </button>
            <NuxtLink>Написать письмо<br />info@floratrans.ru</NuxtLink>
            <NuxtLink>+7 977 909 97 60</NuxtLink>
            <NuxtLink to="/">Написать WhatsApp</NuxtLink>
          </div>
        </div>
      </div>
      <img
        src="/images/main/header_cont_r.png"
        class="header-right-cont"
        alt="image"
      />
    </div>

    <div class="main-page__delivery-content">
      <div class="delivery-block__title-box">
        <h4>Доставка растений из Европы</h4>
      </div>
      <div class="delivery-block__subtitle-box">
        <h5>Полный спектр логистических услуг</h5>
      </div>
      <div class="delivery-block__delivery-info-block">
        <div class="delivery-info-block__columns">
          <div v-for="block in deliveryInfo" class="delivery-info-col">
            <div class="delivery-icon">
              <img :src="block.image" alt="image" />
            </div>
            <div class="delivery-description">
              <div class="delivery-description-title">
                <p>{{ block.title }}</p>
              </div>
              <div class="delivery-description-text">
                <p v-for="text in block.text">{{ text }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="main-page__our-services-content">
      <div class="our-services-content__title">
        <h4>[ Наши услуги ]</h4>
      </div>
      <div class="our-services-content__services-box">
        <div class="services-box__service-list">
          <div
            v-for="service in serviceList"
            @click="showServiceProductFunc(service.id)"
            class="service-list__items"
            :class="{ 'checked-service': service.id === checkedService.id }"
          >
            <img :src="service.image" alt="image" />
            <p>
              <span v-for="text in service.text">{{ text }}<br /></span>
            </p>
          </div>
        </div>
        <div class="services-box__service-description">
          <div class="service-description__image-box">
            <img :src="checkedService.image" alt="image" />
          </div>
          <div class="service-description__title">
            <p>{{ checkedService.title }}</p>
          </div>
          <div class="service-description__product-list">
            <p v-for="text in checkedService.list">
              <ui-icons name="arrow-right" />
              <span>{{ text }}</span>
            </p>
          </div>
        </div>
      </div>
      <div class="our-service-content__logistic-service-title">
        <div class="title-icon">
          <ui-icons name="box" />
        </div>
        <h4>Полный спектр услуг в сфере логистики</h4>
      </div>
      <div class="our-services-content__logistic-services">
        <div class="logistic-services__columns">
          <div
            v-for="service in logisticServices"
            class="logistic-service__box"
          >
            <div class="logistic-service__icon">
              <ui-icons name="checkbox-circle" />
            </div>
            <div class="logistic-service__description">
              <p>
                <span v-for="text in service.text">{{ text }}<br /></span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="main-page__about-content">
      <div class="about-content__title">
        <h4>[ О компании ]</h4>
      </div>
      <div class="about-content__about-description">
        <div class="about-description__image">
          <img src="/images/about/truck.png" alt="image" />
        </div>
        <div class="about-description__text">
          <p class="about-description__first-text">
            Группа компаний «Флора Транс» – это команда профессиональных
            логистов и специалистов по внешней экономической деятельности,
            благодаря которой наши клиенты всегда получают качественный сервис и
            конкурентную стоимость услуг.
          </p>
          <p class="about-description__second-text">
            Мы специализируемся на международных перевозках скоропортящихся
            товаров, регулярно производим мониторинг рынка и предлагаем нашим
            клиентам оптимальные логистические решения по доставке грузов из
            зарубежных стран. Соблюдение договоренностей для нас является
            «железным» правилом. Мы имеем солидный опыт, всегда учитываем
            пожелания клиентов и стоим на пути постоянного развития.
          </p>
        </div>
      </div>
    </div>

    <div class="main-page__advantages-content">
      <div class="advantages-content__title">
        <h4>[ Наши преимущества ]</h4>
      </div>
      <div class="advantages-content__advantages-services">
        <div class="advantages-services__image">
          <img src="/images/advantages/advantages.png" alt="image" />
        </div>
        <div class="advantages-services__columns">
          <div
            v-for="text in advantages"
            class="advantages-service__column"
            :key="text.title"
          >
            <div class="advantages-column-title">
              <p>
                <span v-for="t in text.title">{{ t }}<br /></span>
              </p>
            </div>
            <div class="advantages-column-line"></div>
            <div class="advantages-column__advantages-image-box">
              <img
                class="advantages-image-box__image"
                :src="text.image"
                alt="advantages"
              />
            </div>
            <div class="advantages-column-text">
              {{ text.text }}
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="main-page__question-content">
      <div class="question-content__title">
        <h4>[ У Вас есть вопросы? ]</h4>
        <h4>Свяжитесь с нами</h4>
      </div>
      <div class="question-content__subtitle">
        <p>
          Специалисты «Флора Транс» предоставят консультацию и помогут решить
          вашу задачу
        </p>
      </div>
    </div>

    <div class="main-page__footer-content">
      <div class="footer-content__footer-top-aside">
        <div class="footer-top-aside__footer-left-column">
          <div class="footer-left-column__logo-box">
            <ui-icons name="logo-white" />
          </div>
          <div class="footer-left-column__description-text">
            <p>
              Доставка декоративных растений из Европы Оформление
              сопроводительных документов Доставка сборных грузов c растениями
              Международные грузовые перевозки
            </p>
          </div>
          <div class="footer-left-column__society-buttons">
            <button>
              <ui-icons name="facebook" />
            </button>
            <button>
              <ui-icons name="vk" />
            </button>
            <button>
              <ui-icons name="instagram" />
            </button>
          </div>
        </div>
        <div class="footer-top-aside__footer-right-column">
          <div class="footer-right-column__footer-navigation-list">
            <p>Информация</p>
            <ul class="footer-navigation-list">
              <li>Главная</li>
              <li>Услуги</li>
              <li>О компании</li>
              <li>Контакты</li>
            </ul>
          </div>
          <div class="footer-right-column__footer-information-block">
            <div class="footer-information-block__item">
              <ui-icons name="location" />
              <p>г. Смоленск<br />ул. Нормандия-Неман 35</p>
            </div>
            <div class="footer-information-block__item">
              <ui-icons name="phone" />
              <p>+7 (977) 909 97 60</p>
            </div>
            <div class="footer-information-block__item">
              <ui-icons name="message-small" />
              <p>info@floratrans.ru</p>
            </div>
          </div>
        </div>
      </div>
      <div class="footer-content__footer-bottom-aside">
        <p>
          © 2014-2023. Все права защищены. Флора Транс. Международная
          логистика.
        </p>
        <p><NuxtLink to="/">Политика конфиденциальности</NuxtLink></p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { advantagesData } from "~/components/templates/index/config/advantages";
import { logisticData } from "~/components/templates/index/config/logistic";
import { deliveryData } from "~/components/templates/index/config/delivery";
import { serviceData } from "~/components/templates/index/config/service";
import { deliveryInfoData } from "~/components/templates/index/config/deliveryInfo";

if (process.client) {
  window.addEventListener("scroll", () => {
    let header: HTMLElement | null = document.getElementById("header") || null;
    if (header) {
      header.style.cssText =
        window.scrollY < 50
          ? "width: 90%; transition: width 100ms; height: 114px"
          : "width: 100%; transition: width 100ms; height: 90px";
    }
  });
}

let deliveryInfo = ref(deliveryInfoData);

let serviceList = ref(serviceData);

let serviceDelivery = ref(deliveryData);

let checkedService = ref(serviceDelivery.value[0]);

let logisticServices = ref(logisticData);

let advantages = ref(advantagesData);

let isShowBurgerMenu = ref(false);
const onOpenMenuFunc = () => (isShowBurgerMenu.value = true);
const onCloseBurgerMenu = () => (isShowBurgerMenu.value = false);
const showServiceProductFunc = (serviceId: number) =>
  (checkedService.value = serviceDelivery.value[serviceId]);

</script>

<style scoped>
@import "assets/css/global.css";
@import "assets/css/header.css";
@import "assets/css/delivery.css";
@import "assets/css/services.css";
@import "assets/css/about.css";
@import "assets/css/advantages.css";
@import "assets/css/question.css";
@import "assets/css/footer.css";

.main-page {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

@media (max-width: 768px) {
  .question-content__title, .advantages-content__title, .about-content__title, .our-services-content__title {
    font-size: 30px;
  }
}
@media (max-width: 425px) {
  .question-content__title, .advantages-content__title, .about-content__title, .our-services-content__title {
    font-size: 20px;
  }
}
</style>
