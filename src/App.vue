<script setup>
import { onMounted, ref } from 'vue'
import Footer from './components/layout/Footer.vue'

const bannerItems = ref([
  {
    title: 'سیماب',
    img: '/assets/img/logos/logo-simmab.png',
    link: 'https://simmab.ir/',
  },
  {
    title: 'گشتاب',
    img: '/assets/img/logos/logo-gshtab.png',
    link: 'https://gashtab.ir/',
  },
  {
    title: 'آبان',
    img: '/assets/img/logos/logo-aban.png',
    link: '#',
  },
])
// این کتابخانه‌ها (jQuery, Bootstrap, Swiper, Lity, Fancybox, WOW, scrollIt)
// در index.html به صورت global script لود شده‌اند (window.$ / window.jQuery و ...)
// چون Vue خودش DOM را render می‌کند، باید بعد از mount شدن کامپوننت
// دوباره پلاگین‌هایی مثل Swiper و WOW را init کنیم؛ در غیر این صورت
// اسکریپت‌های assets/js/main.js زودتر از رندر Vue اجرا می‌شوند و اثر نمی‌کنند.
onMounted(() => {
  // تاخیر کوچک تا مطمئن شویم Vue رندر را تمام کرده
  setTimeout(() => {
    // WOW.js (انیمیشن‌های scroll)
    if (window.WOW) {
      new window.WOW().init()
    }

    // Swiper اسلایدر اسکرین‌شات‌ها
    if (window.Swiper) {
      new window.Swiper('.screenshots-slider .swiper-container', {
        slidesPerView: 'auto',
        centeredSlides: true,
        loop: true,
        spaceBetween: 20,
      })
    }

    // fancybox / lity برای لینک‌های data-lity (ویدیوی پروموشن)
    if (window.jQuery) {
      if (window.jQuery.fn.fancybox) {
        window.jQuery('[data-fancybox]').fancybox()
      }
    }

    // اسکرول نرم به سکشن‌ها (data-scroll-nav) در صورتی که scrollIt لود شده باشد
    if (window.scrollIt) {
      window.scrollIt({
        topOffset: -70,
      })
    }

    // مخفی کردن لودر بعد از آماده شدن صفحه
    const loading = document.getElementById('loading-wrapper')
    if (loading) loading.classList.remove('show')
  }, 100)
})
</script>

<template>
  <!-- ====== لودر ====== -->
  <div id="preloader">
    <div id="loading-wrapper" class="show">
      <div id="loading-text"><img src="/assets/img/logos/atey_logo.png" alt="" /></div>
      <div id="loading-content"></div>
    </div>
  </div>

  <!-- ====== نوار بالای هدر ====== -->
  <div class="top-navbar style-4">
    <div class="container">
      <div class="content text-white"></div>
    </div>
  </div>

  <!-- ====== نویگیشن ====== -->
  <nav class="navbar navbar-expand-lg navbar-light style-4" id="main-nav">
    <div class="container">
      <a class="navbar-brand" href="#" data-scroll-nav="0">
        <img src="/assets/img/logos/atey_logo.png" alt="" />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav m-auto mb-2 mb-lg-0 text-uppercase">
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="1">خدمات</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="2">درباره ما</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="3">ویژگی ها</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="4">نرم افزار ها</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="5">سنسور ها</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="6">تاییدیه ها</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#0" data-scroll-nav="7">پرسش و پاسخ</a>
          </li>
        </ul>
        <div class="nav-side">
          <div class="d-flex align-items-center">
            <!-- <a
              href="#0"
              class="btn rounded-pill brd-gray hover-blue4 sm-butn fw-bold"
              data-scroll-nav="8"
            >
              <span>تحميل <i class="bi bi-download ms-1"></i></span>
            </a> -->
          </div>
        </div>
      </div>
    </div>
  </nav>

  <!-- ====== هدر ====== -->
  <header class="style-4" data-scroll-index="0">
    <div class="content">
      <div class="container">
        <div class="row gx-0">
          <div class="col-lg-6">
            <div class="info">
              <h1 class="mb-30">شرکت <span>آتــــــی</span></h1>
              <p class="text">شرکت دانش بنیان پایدار تجهیز آتی خراسان</p>

              <div class="used_app w-100" style="margin-bottom: 40px">
                <ul>
                  <li v-for="item in bannerItems" class="tooltipParent bg-white p-1">
                    <a :href="item.link" target="_blank">
                      <img :src="item.img" alt="image" />
                      <span class="tooltiptext">{{ item.title }}</span>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="img">
              <img src="/assets/img/header/header_42.png" alt="" />
            </div>
          </div>
        </div>
      </div>
      <img src="/assets/img/header/header_4_bubble.png" alt="" class="bubble" />
    </div>

    <div class="wave-wrap">
      <img src="/assets/img/header/header_4_wave.png" alt="" class="wave" />
    </div>
  </header>

  <main>
    <!-- ====== کلاینت‌ها ====== -->
    <section class="clients style-4">
      <div class="container">
        <div class="text-center">
          <h5 class="fw-bold mb-60">شرکت‌هایی که افتخار همکاری داشتیم</h5>
        </div>

        <div class="client-logos pb-70">
          <div class="clients-scroll">
            <div class="client-item">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>
              <p class="client-name">آب منطقه‌ای خراسان رضوی</p>
            </div>

            <div class="client-item">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>
              <p class="client-name">آب منطقه‌ای خراسان شمالی</p>
            </div>

            <div class="client-item">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>
              <p class="client-name">آب منطقه‌ای اصفهان</p>
            </div>

            <div class="client-item">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>
              <p class="client-name">مدیریت منابع آب ایران</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ====== ویژگی‌ها ====== -->
    <section class="features pt-70 pb-70 style-4" data-scroll-index="1">
      <div class="container">
        <div class="section-head text-center style-4">
          <!-- <small class="title_small bg-white">نوتيرو - تطبيق مذكرة سهل الاستخدام</small> -->
          <h2 class="mb-70">خدمات <span>ارئه</span>میدیم</h2>
        </div>
        <div class="content features-content">
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/22.jpg" alt="" />
            </div>
            <h6>طراحی و توسعه سامانه‌های برخط</h6>
          </div>

          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/1.jpg" alt="" />
            </div>
            <h6>تحلیل داده‌های کلان و ژئودیتا</h6>
          </div>

          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/2.jpg" alt="" />
              <!-- <span
                class="label icon-40 alert-success text-success rounded-circle small text-uppercase fw-bold"
              >
                جديد
              </span> -->
            </div>
            <h6>توسعه اپلیکیشن‌های اندروید و IOS</h6>
          </div>

          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/5.png" alt="" />
            </div>
            <h6>طراحی و ساخت سنسورهای هواشناسی</h6>
          </div>

          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/4.jpg" alt="" />
            </div>
            <h6>طراحی و ساخت دیتالاگر و ادوات الکترونیکی</h6>
          </div>

          <!-- کارت 6 -->
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/6.jpg" alt="" />
            </div>
            <h6>طراحی و ساخت ایستگاه های خودکار هواشناسی</h6>
          </div>

          <!-- کارت 7 -->
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe/7.png" alt="" />
            </div>
            <h6>اینترنت اشیاء</h6>
          </div>
        </div>
      </div>
      <img src="/assets/img/feat_circle.png" alt="" class="img-circle" />
    </section>

    <!-- ====== درباره‌ی ما ====== -->
    <section class="about section-padding style-4">
      <div class="content frs-content" id="about" data-scroll-index="2">
        <div class="container">
          <div class="row align-items-center justify-content-between">
            <div class="col-lg-6">
              <div class="img mb-30 mb-lg-0">
                <img src="/assets/img/about/dashboard.png" alt="" />
              </div>
            </div>
            <div class="col-lg-5">
              <div class="info">
                <div class="section-head style-4">
                  <!-- <small class="title_small">نوتيرو - تطبيق مذكرة سهل الاستخدام</small> -->
                  <h2 class="mb-30">دربـــاره ما</h2>
                </div>
                <p class="text mb-40">
                  شرکت پایدار تجهیز آتی خراسان در سال 1401 با هدف تولید سنسور ها، دیتالاگرها تجهیزات
                  الکتورنیکی حوزه آب و هواشناسی، همچنین طراحی و توسعهه سامانه‌ها و نرم‌افزارهای این
                  حوزه تاسیس گردید. این شرکت در سال 1402 در پردیس فناوری جامع پارک علم و فناوری
                  خراسان مستقر و در سال 1403 با تکیه بر توان نیروهای نخبه خود موفق به اخذ مجوز
                  دانش‌بنیانی از معاونت علمی ریاست جمهوری شد. محصولات این شرکت دارای تاییدیه
                  بالاترین سطح آمادگی فناوری (TRL9) از سافا (سامانه ارزیابی فناوری ایران) می‌باشد.
                </p>
                <ul>
                  <li class="d-flex align-items-center mb-3">
                    <small
                      class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-3"
                    >
                      <i class="fas fa-tag"></i>
                    </small>
                    <h6 class="fw-bold">
                      طراحی و توسعه سامانه‌های نرم‌افزاری و تحت وب حوزه آب و هواشناسی
                    </h6>
                  </li>
                  <li class="d-flex align-items-center mb-3">
                    <small
                      class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-3"
                    >
                      <i class="fas fa-sync"></i>
                    </small>
                    <h6 class="fw-bold">طراحی و توليد سنسورها و تجهيزات حوزه آب و هواشناسی</h6>
                  </li>
                  <li class="d-flex align-items-center">
                    <small
                      class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-3"
                    >
                      <i class="fas fa-text-width"></i>
                    </small>
                    <h6 class="fw-bold">هوش مصنوعی‌ و اينترنت اشياء</h6>
                  </li>
                </ul>
                <!-- <a
                  href="/page-contact-5"
                  class="btn rounded-pill bg-blue4 fw-bold text-white mt-50"
                >
                  <small>تسجيل مجاني</small>
                </a> -->
              </div>
            </div>
          </div>
        </div>
        <img src="/assets/img/about/about_s4_lines.png" alt="" class="lines" />
        <img src="/assets/img/about/about_s4_bubble.png" alt="" class="bubble" />
      </div>

      <div class="content sec-content" data-scroll-index="3">
        <div class="container">
          <div class="row align-items-center justify-content-between">
            <div class="col-lg-5 order-2 order-lg-0">
              <div class="info">
                <div class="section-head style-4">
                  <!-- <small class="title_small">إدارة أفضل للملاحظات</small> -->
                  <h2 class="mb-30">ویژگی های<span>مـــا</span></h2>
                </div>
                <p class="text mb-40">
                  طراحی و توسعه نرم‌افزار مدیریت اطلاعات و داده های منابع آب و سامانه مدیریت فرایند
                  های سازمانی
                </p>
                <div class="faq style-3 style-4">
                  <div class="accordion d-flex flex-column gap-3" id="accordionExample">
                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/safe.gif" alt="image" />
                      </div>

                      <div class="text">
                        <h4>امنیت و رمزنگاری</h4>
                        <p>طبق آخرین استانداردهای امنیتی</p>
                      </div>
                    </div>

                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/speedometer.gif" alt="image" />
                      </div>
                      <div class="text">
                        <h4>سرعت و عملکرد</h4>
                        <p>سرعت بالا و عملکرد بهینه</p>
                      </div>
                    </div>
                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/responsive.gif" alt="image" />
                      </div>
                      <div class="text">
                        <h4>تطابق و سازگاری</h4>
                        <p>با انواع دستگا‌ها و سیستم‌عامل‌ها</p>
                      </div>
                    </div>

                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/network.gif" alt="image" />
                      </div>
                      <div class="text">
                        <h4>آنلاین و آفلاین</h4>
                        <p>کارکرد در حالت آنلاین و آفلاین</p>
                      </div>
                    </div>

                    <!-- feature box -->
                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/checklist.gif" alt="image" />
                      </div>
                      <div class="text">
                        <h4>صحت‌سنجی داده</h4>
                        <p>اعتبارسنجی زمان، مکان و تصویر</p>
                      </div>
                    </div>

                    <!-- feature box -->
                    <div
                      class="d-flex align-items-center security-item"
                      data-aos="fade-right"
                      data-aos-duration="1500"
                    >
                      <div class="icon">
                        <img src="/assets/img/gifs/computer.gif" alt="image" />
                      </div>
                      <div class="text">
                        <h4>رابط کاربری</h4>
                        <p>آسان، زیبا و کاربرپسند</p>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- <a
                  href="https://chrome.google.com/webstore/category/extensions"
                  class="btn btn-img mt-40 rounded-pill"
                  target="_blank"
                >
                  <div class="icon img-contain">
                    <img src="/assets/img/icons/chrome_icon.png" alt="" />
                  </div>
                  <div class="inf">
                    <small>متاح في</small>
                    <h6>متجر كروم الالكتروني</h6>
                  </div>
                </a> -->
              </div>
            </div>
            <div class="col-lg-6 order-0 order-lg-2">
              <div class="img mb-30 mb-lg-0">
                <img src="/assets/img/about/2phone.png" alt="" />
              </div>
            </div>
          </div>
        </div>
        <img src="/assets/img/about/about_s4_bubble2.png" alt="" class="bubble2" />
      </div>

      <div class="content trd-content">
        <div class="container">
          <div class="row align-items-center justify-content-between">
            <div class="col-lg-6">
              <div class="img mb-30 mb-lg-0">
                <img src="/assets/img/dashbord.png" alt="" />
              </div>
            </div>
            <div class="col-lg-5">
              <div class="info">
                <div class="section-head style-4">
                  <!-- <small class="title_small">ثيمات جميلة</small> -->
                  <h2 class="mb-30">داشبورد <span>کنترل، نظارت و تحلیل</span></h2>
                </div>
                <p class="text mb-40">
                  شامل ابزارهایی برای کنترل و نظارت بر فرآیندهای داده‌برداری، منابع انسانی، صحت‌سنجی
                  و مقایسه داده‌ها، تولید گزارشات تحلیلی و مدیریتی و ماژول‌های محاسبات سنگین است
                </p>
                <div class="features_block">
                  <div class="d-flex flex-column gap-3">
                    <div class="d-flex">
                      <div class="d-flex feature-item" data-aos="fade-up" data-aos-duration="1500">
                        <div class="image">
                          <img src="/assets/img/pic/settings.png" alt="image" />
                        </div>
                        <div class="text">
                          <h4>کنترل و نظارت</h4>
                          <p>
                            شامل ابزارهایی جهت کنترل و نظارت بر فرآیندهای داده‌برداری و منابع انسانی
                          </p>
                        </div>
                      </div>
                    </div>

                    <div class="d-flex">
                      <div class="d-flex feature-item" data-aos="fade-up" data-aos-duration="1700">
                        <div class="image">
                          <img src="/assets/img/pic/infographics.png" alt="image" />
                        </div>
                        <div class="text">
                          <h4>صحت‌سنجی و مقایسه</h4>
                          <p>شامل ابزارهایی جهت صحت‌سنجی، مقایسه با داده‌های گذشته و منابع اطراف</p>
                        </div>
                      </div>
                    </div>

                    <div class="d-flex">
                      <div class="d-flex feature-item" data-aos="fade-up" data-aos-duration="1900">
                        <div class="image">
                          <img src="/assets/img/pic/monitor.png" alt="image" />
                        </div>
                        <div class="text">
                          <h4>گزارشات تحلیلی و مدیریتی</h4>
                          <p>تولید گزارشات کارشناسی، مدیریتی، تحلیلی و ترکیبی</p>
                        </div>
                      </div>
                    </div>

                    <div class="d-flex">
                      <div class="d-flex feature-item" data-aos="fade-up" data-aos-duration="1900">
                        <div class="image">
                          <img src="/assets/img/pic/intelligence.png" alt="image" />
                        </div>
                        <div class="text">
                          <h4>ماژول محاسبات سنگین</h4>
                          <p>ماژول محاسبات سنگین همچون هیدروگراف واحد آبخوان، کموگراف و ...</p>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- <a
                  href="/page-services-5"
                  class="btn rounded-pill bg-blue4 fw-bold text-white mt-50"
                >
                  <small>اكتشف الآن</small>
                </a> -->
              </div>
            </div>
          </div>
        </div>
        <img src="/assets/img/about/about_s4_bubble.png" alt="" class="bubble" />
      </div>

      <div class="integration pt-60">
        <div class="section-head text-center style-4">
          <small class="title_small">دفعة لمرة واحدة</small>
          <h2 class="mb-20">متوافق مع <span>التطبيقات الشعبية</span></h2>
          <p>نوتيرو يتكامل مع التطبيقات الشعبية. تساعدك على التواصل والتعاون بسهولة</p>
        </div>
        <div class="container">
          <div class="content">
            <div class="img">
              <img src="/assets/img/about/intg1.png" alt="" class="mt-30" />
            </div>
            <div class="img">
              <img src="/assets/img/about/intg5.png" alt="" class="mt-60" />
            </div>
            <div class="img">
              <img src="/assets/img/about/intg4.png" alt="" class="mt-20" />
            </div>
            <div class="img">
              <img src="/assets/img/about/intg3.png" alt="" class="mt-80" />
            </div>
            <div class="img">
              <img src="/assets/img/about/intg2.png" alt="" />
            </div>
          </div>
        </div>
        <img src="/assets/img/about/intg_back.png" alt="" class="intg-back" />
      </div>
      <img src="/assets/img/about/about_s4_wave.png" alt="" class="top-wave" />
      <img src="/assets/img/about/about_s4_wave.png" alt="" class="bottom-wave" />
    </section>

    <!-- ====== اسکرین‌شات‌ها ====== -->
    <div class="screenshots style-4" data-scroll-index="4">
      <div class="screenshots-slider style-4">
        <div class="swiper-container">
          <div class="swiper-wrapper">
            <div class="swiper-slide" v-for="n in 10" :key="n">
              <div class="img">
                <img :src="`/assets/img/screenshots/${n}.png`" alt="" />
              </div>
            </div>
          </div>
        </div>
      </div>
      <img src="/assets/img/screenshots/hand.png" alt="" class="mob-hand" />
    </div>

    <!-- ====== نظرات مشتریان ====== -->
    <section class="testimonials style-4 pt-70" data-scroll-index="5">
      <div class="container">
        <div class="content">
          <div class="row">
            <div class="col-lg-5">
              <div class="section-head style-4">
                <!-- <small class="title_small">اراء العملاء</small> -->
                <h2 class="mb-30">سنـــسورها</h2>
              </div>
              <p class="text mb-40">
                توسعه ماژول‌های محاسباتی همچون بیلان منابع آب، هیدروگراف، کموگراف و... بکارگیری
                روش‌های نوین همچون هوش مصنوعی، اینترنت اشیا و بهینه‌سازی در حوزه آب و هواشناسی
              </p>

              <div class="d-flex align-items-center mt-70">
                <ul class="design_block small-design-block">
                  <li data-aos="fade-up" data-aos-duration="1500">
                    <span class="check-icon">✓</span>
                    <div>
                      <h4>پروتکل MQTT (اینترنت اشیاء)</h4>
                      <p>پروتکل مخصوص دستگاه‌های با قابلیت اینترنت اشیاء</p>
                    </div>
                  </li>

                  <li data-aos="fade-up" data-aos-duration="1500">
                    <span class="check-icon">✓</span>
                    <div>
                      <h4>پروتکل HTTP(s)</h4>
                      <p>پروتکل مخصوص دستگاه‌های با قابلیت اتصال اینترنتی</p>
                    </div>
                  </li>

                  <li data-aos="fade-up" data-aos-duration="1500">
                    <span class="check-icon">✓</span>
                    <div>
                      <h4>پروتکل FTP</h4>
                      <p>پروتکل مخصوص دستگاه‌های با قابلیت ذخیره‌سازی FTP</p>
                    </div>
                  </li>

                  <li data-aos="fade-up" data-aos-duration="1500">
                    <span class="check-icon">✓</span>
                    <div>
                      <h4>پروتکل SOCKET</h4>
                      <p>پروتکل مخصوص دستگاه‌های با قابلیت وب‌سوکت</p>
                    </div>
                  </li>

                  <li data-aos="fade-up" data-aos-duration="1500">
                    <span class="check-icon">✓</span>
                    <div>
                      <h4>پیام کوتاه SMS</h4>
                      <p>پروتکل مخصوص دستگاه‌های با قابلیت ارسال پیامک</p>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
            <div class="col-lg-7">
              <div class="testi-cards">
                <div class="client_card">
                  <div class="user_img">
                    <img src="/assets/img/testimonials/user4.png" alt="" />
                  </div>
                  <div class="inf_content">
                    <div class="stars mb-2">
                      <i class="fas fa-star" v-for="n in 5" :key="n"></i>
                    </div>
                    <h6>
                      "يمكنك حتى إرسال رسائل بريد إلكتروني إلى Evernote وجمع <br />
                      كل الأشياء التي تحتاجها في مكان واحد."
                    </h6>
                    <p>
                      يورجن ك.
                      <span class="text-muted">/ أول قسم التسويق في <span>Brator</span></span>
                    </p>
                  </div>
                </div>
                <div class="client_card">
                  <div class="user_img">
                    <img src="/assets/img/testimonials/user5.png" alt="" />
                  </div>
                  <div class="inf_content">
                    <div class="stars mb-2">
                      <i class="fas fa-star" v-for="n in 5" :key="n"></i>
                    </div>
                    <h6>"نوتيرو - الخيار الأول الذي أختاره لتطبيق الملاحظات. رائع"</h6>
                    <p>
                      فودن ص. <span class="text-muted">/ مدير في <span>Ecoland Resort</span></span>
                    </p>
                  </div>
                </div>
                <div class="client_card">
                  <div class="user_img">
                    <img src="/assets/img/testimonials/user6.png" alt="" />
                  </div>
                  <div class="inf_content">
                    <div class="stars mb-2">
                      <i class="fas fa-star" v-for="n in 5" :key="n"></i>
                    </div>
                    <h6>
                      ".هذا التطبيق جيد بجدية. إنه ببساطة، نظيف و <br />
                      متعة حقيقية في الاستخدام."
                    </h6>
                    <p>
                      Kerry T. <span class="text-muted">/ مصمم في <span>Teckzone Inc</span></span>
                    </p>
                  </div>
                </div>
                <img src="/assets/img/contact_globe.svg" alt="" class="testi-globe" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ====== قیمت‌گذاری ====== -->
    <section class="pricing section-padding style-4 pb-50" data-scroll-index="6">
      <div class="container">
        <div class="section-head text-center style-4">
          <!-- <small class="title_small">خطة الاسعار</small> -->
          <h2 class="mb-30">تــاییدیه و افتخـــارات</h2>
        </div>
        <div class="content">
          <div class="row gx-0">
            <!-- مجوزها و تاییدیه‌ها -->
            <div class="col-lg-6">
              <div class="price-card">
                <div class="price-header pb-4">
                  <h6>
                    <!-- <img src="/assets/img/icons/price_s4_1.png" alt="" class="icon" /> -->
                    مجوزها و تأییدیه‌ها
                  </h6>

                  <h2>اعتبار <small>و استاندارد</small></h2>

                  <p>برخی از مهم‌ترین مجوزها و تأییدیه‌های سامانه سیماب</p>
                </div>

                <div class="price-body py-4">
                  <ul>
                    <!-- دانش بنیان -->
                    <li class="achievement-item mb-4">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/danesh.jpg" alt="مجوز دانش‌بنیان" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-check"></i>
                          </small>

                          <strong>مجوز دانش‌بنیان</strong>
                        </div>

                        <small class="achievement-date"> ۱۴۰۳/۰۵/۱۵ </small>

                        <p>
                          سامانه سیماب توسط معاونت علمی ریاست جمهوری به عنوان یک محصول دانش‌بنیان
                          تأیید گردید.
                        </p>
                      </div>
                    </li>

                    <!-- TRL9 -->
                    <li class="achievement-item mb-4">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/trl9.jpg" alt="تاییدیه TRL9" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-check"></i>
                          </small>

                          <strong>تأییدیه TRL9</strong>
                        </div>

                        <small class="achievement-date"> ۱۴۰۳/۰۹/۲۰ </small>

                        <p>
                          براساس ارزیابی سافا، سامانه سیماب حائز بالاترین سطح آمادگی فناوری (TRL9)
                          می‌باشد.
                        </p>
                      </div>
                    </li>

                    <!-- افتا -->
                    <li class="achievement-item">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/afta.jpg" alt="مجوز افتا" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-clock"></i>
                          </small>

                          <strong>مجوز افتا</strong>
                        </div>

                        <small class="achievement-date"> در حال انجام </small>

                        <p>
                          سامانه سیماب در حال اخذ مجوز افتا از سازمان فناوری اطلاعات ایران می‌باشد.
                        </p>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>

            <!-- افتخارات -->
            <div class="col-lg-6">
              <div class="price-card">
                <div class="price-header pb-4">
                  <h6>
                    <!-- <img src="/assets/img/icons/price_s4_2.png" alt="" class="icon" /> -->
                    افتخارات و دستاوردها
                  </h6>

                  <h2>افتخارات <small>شرکت</small></h2>

                  <p>بخشی از افتخارات و دستاوردهای علمی و فناورانه شرکت</p>
                </div>

                <div class="price-body py-4">
                  <ul>
                    <!-- استقلال -->
                    <li class="achievement-item mb-4">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/esteghlal.jpg" alt="نشان مردمی استقلال" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-award"></i>
                          </small>

                          <strong>نشان مردمی استقلال</strong>
                        </div>

                        <small class="achievement-date"> رتبه برتر </small>

                        <p>
                          نشان مردمی استقلال به پاس تلاش‌های علمی و پژوهشی مؤثر در جهت استقلال و
                          خودکفایی کشور اعطا می‌گردد.
                        </p>
                      </div>
                    </li>

                    <!-- فن آب -->
                    <li class="achievement-item mb-4">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/fanab.jpg" alt="رویداد ملی فن‌آب" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-trophy"></i>
                          </small>

                          <strong>رویداد ملی فن‌آب</strong>
                        </div>

                        <small class="achievement-date"> رتبه برتر </small>

                        <p>
                          طرح ایستگاه خودکار آب و هواشناسی مجهز به اینترنت اشیاء موفق به کسب رتبه
                          برتر گردید.
                        </p>
                      </div>
                    </li>

                    <!-- ثبت اختراع -->
                    <li class="achievement-item">
                      <div class="achievement-img">
                        <img src="/assets/img/pic/patent.jpg" alt="گواهی ثبت اختراع" />
                      </div>

                      <div class="achievement-content">
                        <div class="achievement-title">
                          <small class="achievement-icon">
                            <i class="fas fa-certificate"></i>
                          </small>

                          <strong>گواهی ثبت اختراع</strong>
                        </div>

                        <small class="achievement-date"> طرح برتر بنیاد ملی نخبگان </small>

                        <p>
                          دو نمونه از طرح‌های مربوط به ساخت سنسورها موفق به ثبت اختراع گردیده‌اند.
                        </p>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ====== سوالات متداول ====== -->
    <section class="faq section-padding style-4 pt-50" data-scroll-index="7">
      <div class="container">
        <div class="section-head text-center style-4">
          <!-- <small class="title_small">أسئلة شائعة</small> -->
          <h2 class="mb-30">پرسش و <span>پــاسخ</span></h2>
        </div>
        <div class="content">
          <div class="faq style-3 style-4">
            <div class="accordion" id="accordionSt4">
              <div class="row gx-5">
                <div class="col-lg-6">
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading11">
                      <button
                        class="accordion-button collapsed rounded-0 py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse11"
                        aria-expanded="true"
                        aria-controls="collapse11"
                      >
                        شرکت پایدار تجهیز اتی خراسان چه خدماتی ارائه می‌دهد؟
                      </button>
                    </h2>
                    <div
                      id="collapse11"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading11"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        شرکت پایدار تجهیز آتی خراسان در زمینه طراحی و توسعه نرم‌افزارهای تخصصی،
                        سامانه‌های مدیریت و تحلیل داده، هوشمندسازی فرآیندها و ارائه راهکارهای
                        نرم‌افزاری فعالیت می‌کند. یکی از محصولات اصلی شرکت، سامانه یکپارچه مدیریت
                        داده و منابع آب ایران (سیماب) است که با هدف الکترونیکی‌سازی، مدیریت، کنترل،
                        گزارش‌گیری و تحلیل داده‌های منابع آب توسعه یافته است.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading12">
                      <button
                        class="accordion-button py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse12"
                        aria-expanded="false"
                        aria-controls="collapse12"
                      >
                        سامانه سیماب چیست و چه کاربردی دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse12"
                      class="accordion-collapse collapse show rounded-0"
                      aria-labelledby="heading12"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        سامانه یکپارچه مدیریت داده و منابع آب ایران (سیماب)، یک سامانه تخصصی برای
                        مدیریت فرآیندهای داده‌برداری، کنترل، نظارت، گزارش‌گیری و تحلیل داده‌های
                        منابع آب است که فرآیندهای دفتر مطالعات پایه منابع آب را به‌صورت یکپارچه و
                        الکترونیکی مدیریت می‌کند.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading13">
                      <button
                        class="accordion-button collapsed py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse13"
                        aria-expanded="false"
                        aria-controls="collapse13"
                      >
                        سامانه سیماب چیست و چه کاربردی دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse13"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading13"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        سامانه یکپارچه مدیریت داده و منابع آب ایران (سیماب)، یک سامانه تخصصی برای
                        مدیریت فرآیندهای داده‌برداری، کنترل، نظارت، گزارش‌گیری و تحلیل داده‌های
                        منابع آب است که فرآیندهای دفتر مطالعات پایه منابع آب را به‌صورت یکپارچه و
                        الکترونیکی مدیریت می‌کند.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-0 rounded-0">
                    <h2 class="accordion-header" id="heading4">
                      <button
                        class="accordion-button collapsed rounded-0 py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse4"
                        aria-expanded="true"
                        aria-controls="collapse4"
                      >
                        سیماب در چه استان‌ها یا سازمان‌هایی فعال است؟
                      </button>
                    </h2>
                    <div
                      id="collapse4"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading4"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        سامانه سیماب از سال ۱۳۹۹ در دفتر مطالعات پایه منابع آب شرکت آب منطقه‌ای
                        خراسان رضوی راه‌اندازی شده و در حال حاضر در استان‌های خراسان رضوی و اصفهان
                        فعال است.
                      </div>
                    </div>
                  </div>
                </div>
                <div class="col-lg-6">
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading5">
                      <button
                        class="accordion-button collapsed rounded-0 py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse5"
                        aria-expanded="true"
                        aria-controls="collapse5"
                      >
                        آیا نرم‌افزار به اینترنت دائمی نیاز دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse5"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading5"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        سامانه سیماب با توجه به نیازهای عملیاتی کاربران، امکان استفاده در حالت
                        آنلاین و آفلاین را فراهم می‌کند. بنابراین برخی فرآیندها و اطلاعات موردنیاز
                        کاربران در شرایط عدم دسترسی به اینترنت نیز قابل استفاده هستند.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading6">
                      <button
                        class="accordion-button collapsed py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse6"
                        aria-expanded="false"
                        aria-controls="collapse6"
                      >
                        آیا سامانه امکان اتصال به سایر سامانه‌ها و تجهیزات را دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse6"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading6"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        بله. سامانه سیماب با استفاده از پروتکل‌ها و سرویس‌های ارتباطی مختلف، قابلیت
                        تبادل اطلاعات و اتصال به سامانه‌ها، تجهیزات و منابع داده مختلف را دارد. این
                        قابلیت امکان جمع‌آوری و یکپارچه‌سازی داده‌ها از منابع مختلف را فراهم می‌کند.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading7">
                      <button
                        class="accordion-button collapsed py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse7"
                        aria-expanded="false"
                        aria-controls="collapse7"
                      >
                        آیا سامانه قابلیت شخصی‌سازی متناسب با نیاز سازمان را دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse7"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading7"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        بله. ساختار سامانه به‌گونه‌ای طراحی شده است که امکان توسعه و شخصی‌سازی
                        ماژول‌ها، فرآیندها، فرم‌ها، گزارش‌ها و دسترسی‌های کاربران متناسب با نیاز هر
                        سازمان وجود داشته باشد.
                      </div>
                    </div>
                  </div>
                  <div class="accordion-item border-bottom rounded-0">
                    <h2 class="accordion-header" id="heading8">
                      <button
                        class="accordion-button collapsed rounded-0 py-4"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#collapse8"
                        aria-expanded="true"
                        aria-controls="collapse8"
                      >
                        آیا امکان پشتیبانی و توسعه سامانه وجود دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse8"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading8"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        بله. پس از راه‌اندازی سامانه، خدمات پشتیبانی، رفع اشکال، به‌روزرسانی و توسعه
                        قابلیت‌های سامانه متناسب با نیازهای سازمان ارائه می‌شود.
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <Footer></Footer>
  <!-- ====== دکمه‌ی بازگشت به بالا ====== -->
  <a
    href="#"
    class="to_top bg-gray rounded-circle icon-40 d-inline-flex align-items-center justify-content-center"
  >
    <i class="bi bi-chevron-up fs-6 text-dark"></i>
  </a>
</template>
<style lang="css" scoped>
.clients.style-4 .client-name {
  text-align: center;
  margin: 12px 0 0;
}
.security-item .icon img {
  width: 50px;
  height: 50px;
  border-radius: 50px;
}

.img-contain img {
  border-radius: 60px;
}

.security-item .text h4 {
  font-size: 15px;
}

.security-item .text p {
  font-size: 11px;
}

.small-design-block {
  width: 100%;
}

.small-design-block li {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 16px;
}

.small-design-block .check-icon {
  width: 22px;
  height: 22px;
  min-width: 22px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: #198754;
  color: #fff;
  font-size: 13px;
  font-weight: bold;
  margin-top: 2px;
}

.small-design-block h4 {
  font-size: 15px;
  margin: 0 0 4px;
  line-height: 1.5;
}

.small-design-block p {
  font-size: 11px;
  margin: 0;
  line-height: 1.7;
  opacity: 0.7;
}
.features_block .feature-item {
  gap: 12px;
}

.features_block .feature-item .image img {
  width: 42px;
  height: 42px;
  object-fit: contain;
}

.features_block .feature-item .text h4 {
  font-size: 15px;
  margin: 0 0 5px;
  line-height: 1.5;
}

.features_block .feature-item .text p {
  font-size: 12px;
  line-height: 1.7;
  margin: 0;
}

.features_block > div > .d-flex {
  margin-bottom: 20px;
}

.features_block > div > .d-flex:last-child {
  margin-bottom: 0;
}
.clients .clients-scroll {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  gap: 30px;
}

.clients .client-item {
  flex: 0 0 180px;
  text-align: center;
}

.clients .client-item .img {
  display: flex !important;
  align-items: center;
  justify-content: center;
  height: 90px;
}

.clients .client-item img {
  width: 70px;
  height: 70px;
  object-fit: contain;
}

.clients .client-name {
  margin: 10px 0 0;
  font-size: 13px;
  line-height: 1.7;
}

/* Mobile */
@media (max-width: 767.98px) {
  .clients .clients-scroll {
    justify-content: flex-start;
    gap: 15px;

    overflow-x: auto;
    overflow-y: hidden;

    padding: 5px 10px 15px;

    /* اسکرول نرم */
    scroll-behavior: smooth;

    /* مخفی کردن scrollbar */
    scrollbar-width: none;
  }

  .clients .clients-scroll::-webkit-scrollbar {
    display: none;
  }

  .clients .client-item {
    flex: 0 0 115px;
  }

  .clients .client-item .img {
    height: 65px;
  }

  .clients .client-item img {
    width: 50px;
    height: 50px;
  }

  .clients .client-name {
    font-size: 11px;
    line-height: 1.6;
    margin-top: 7px;
  }

  .clients h5 {
    font-size: 15px;
    margin-bottom: 30px !important;
  }
}
.achievement-item {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  list-style: none;
}

/* عکس */
.achievement-img {
  width: 85px;
  height: 85px;
  min-width: 85px;
  border-radius: 10px;
  overflow: hidden;
  background: #f5f7fa;
}

.achievement-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* متن */
.achievement-content {
  flex: 1;
  min-width: 0;
}

.achievement-title {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 3px;
}

.achievement-title strong {
  font-size: 14px;
  font-weight: 700;
}

.achievement-icon {
  width: 25px;
  height: 25px;
  min-width: 25px;
  border-radius: 50%;
  background: #01305a;
  color: #fff;

  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.achievement-icon i {
  font-size: 11px;
}

.achievement-date {
  display: block;
  color: #01305a;
  font-size: 10px;
  margin-bottom: 4px;
}

.achievement-content p {
  font-size: 11px;
  line-height: 1.8;
  margin: 0;
  font-weight: 400;
}

/* موبایل */
@media (max-width: 767.98px) {
  .achievement-item {
    gap: 10px;
  }

  .achievement-img {
    width: 70px;
    height: 70px;
    min-width: 70px;
  }

  .achievement-title strong {
    font-size: 12px;
  }

  .achievement-content p {
    font-size: 10px;
    line-height: 1.7;
  }

  .achievement-icon {
    width: 22px;
    height: 22px;
    min-width: 22px;
  }
}
.faq.style-4 .accordion-item {
  background-color: #fff;
}

.faq.style-4 .accordion-button.collapsed {
  background-color: #fff !important;
}

.faq.style-4 .accordion-button:not(.collapsed) {
  background-color: #e6f1f8 !important;
}

.faq.style-4 .accordion-body {
  background-color: #e6f1f8 !important;
}

/* =================heder */
/* ===== کلاس‌های اصلی (بدون نیاز به banner_section) ===== */
.used_app {
  display: flex;
  align-items: center;
  margin-top: 35px;
  flex-wrap: wrap;
  gap: 5px;
}

.used_app ul {
  display: flex;
  align-items: center;
  margin: 0;
  padding: 0;
  list-style: none;
}

.used_app ul li {
  width: 80px;
  height: 80px;
  border-radius: 100%;
  border: 4px solid #01305a;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px;
  position: relative;
  cursor: pointer;
  transition: all 0.2s ease;
}

/* همپوشانی */
.used_app ul li:not(:first-child) {
  margin-right: -25px;
}

/* تصویر */
.used_app ul li img {
  width: 65%;
  height: 65%;
  object-fit: contain;
  display: block;
}

/* لینک */
.used_app ul li a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  text-decoration: none;
}

/* ===== Tooltip ===== */
.tooltipParent .tooltiptext {
  visibility: hidden;
  width: 200px;
  background-color: var(#caf0f8);
  color: var(#01305a);
  text-align: center;
  border: 3px solid #01305a;
  border-radius: 6px;
  padding: 6px 10px;
  position: absolute;
  z-index: 10;
  top: 115%;
  left: 50%;
  transform: translateX(-50%);
  opacity: 0;
  transition: opacity 0.3s ease;
  font-weight: bold;
  font-size: 14px;
  white-space: nowrap;
  pointer-events: none;
}

.tooltipParent .tooltiptext::after {
  content: '';
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  border-width: 6px;
  border-style: solid;
  border-color: transparent transparent var(--bg-purple, #caf0f8) transparent;
}

.tooltipParent:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}

/* ===== واکنش‌گرایی ===== */
@media (max-width: 576px) {
  .used_app ul li {
    width: 60px;
    height: 60px;
    border-width: 3px;
    padding: 3px;
  }
  .used_app ul li:not(:first-child) {
    margin-right: -18px;
  }
  .used_app ul li img {
    width: 60%;
    height: 60%;
  }
  .tooltipParent .tooltiptext {
    width: 160px;
    font-size: 12px;
    top: 110%;
    white-space: normal;
  }
}
</style>
