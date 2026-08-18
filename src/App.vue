<script setup>
import { onMounted } from 'vue'

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
      <div id="loading-text"><img src="/assets/img/logo_loading.png" alt="" /></div>
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
        <img src="/assets/img/logo_lgr.png" alt="" />
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
              <!-- <small class="mb-50 title_small">نوتيرو - تطبيق مذكرة سهل الاستخدام</small> -->
              <h1 class="mb-30">شرکت <span>آتی</span></h1>
              <p class="text">شرکت دانشبنیان پایدار تجهیز آتی خراسان</p>
              <!-- <div class="d-flex align-items-center mt-50">
                <a
                  href="https://www.apple.com/app-store/"
                  class="btn rounded-pill bg-blue4 fw-bold text-white me-4"
                  target="_blank"
                >
                  <small><i class="fab fa-apple me-2 pe-2 border-end"></i> تحميل التطبيق</small>
                </a>
                <a href="https://youtu.be/pGbIOC83-So?t=21" data-lity class="play-btn">
                  <span class="icon me-2"><i class="fas fa-play ms-1"></i></span>
                  <strong class="small">مشاهدة <br /> البرومو</strong>
                </a>
              </div> -->
              <span class="mt-100 me-5">
                <small
                  class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-1"
                >
                  <i class="fas fa-sync"></i>
                </small>
                <small class="text-uppercase">سیــماب</small>
              </span>
              <span class="mt-100 me-5">
                <small
                  class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-1"
                >
                  <i class="fas fa-credit-card"></i>
                </small>
                <small class="text-uppercase">گشــتاب</small>
              </span>
              <span class="mt-100 me-5">
                <small
                  class="icon-30 bg-gray rounded-circle color-blue4 d-inline-flex align-items-center justify-content-center me-1"
                >
                  <i class="fas fa-credit-card"></i>
                </small>
                <small class="text-uppercase">آبــان</small>
              </span>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="img">
              <img src="/assets/img/header/header_4.png" alt="" />
            </div>
          </div>
        </div>
      </div>
      <img src="/assets/img/header/header_4_bubble.png" alt="" class="bubble" />
    </div>
    <img src="/assets/img/header/header_4_wave.png" alt="" class="wave" />
  </header>

  <main>
    <!-- ====== کلاینت‌ها ====== -->
    <section class="clients style-4">
      <div class="container">
        <div class="text-center">
          <h5 class="fw-bold mb-60">شرکت هایی که افتخار همکاری داشتیم</h5>
        </div>

        <div class="client-logos pb-70">
          <div class="d-flex justify-content-around">
            <div class="col-6 col-lg-2">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>

              <p class="client-name">آب منطقه‌ای خراسان رضوی</p>
            </div>
            <div class="col-6 col-lg-2">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>

              <p class="client-name">آب منطقه‌ای خراسان شمالی</p>
            </div>
            <div class="col-6 col-lg-2">
              <a href="#" class="img d-block">
                <img src="/assets/img/icons/abmantaghei.png" alt="" />
              </a>

              <p class="client-name">آب منطقه‌ای اصفهان</p>
            </div>
            <div class="col-6 col-lg-2">
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
        <div class="content">
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe1.png" alt="" />
            </div>
            <h6>دیتالاگــر</h6>
          </div>
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe2.png" alt="" />
            </div>
            <h6>سنســور های آب</h6>
          </div>
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe3.png" alt="" />
              <span
                class="label icon-40 alert-success text-success rounded-circle small text-uppercase fw-bold"
              >
                جديد
              </span>
            </div>
            <h6>ایستگاه هــواشناسی</h6>
          </div>
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe4.png" alt="" />
            </div>
            <h6>اپلیکیشن داده برداری</h6>
          </div>
          <div class="features-card">
            <div class="icon img-contain">
              <img src="/assets/img/icons/fe5.png" alt="" />
            </div>
            <h6>ادوات الکترونیـــکی</h6>
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
                <img src="/assets/img/about/ipad.png" alt="" />
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

      <div class="content sec-content">
        <div class="container">
          <div class="row align-items-center justify-content-between">
            <div class="col-lg-5 order-2 order-lg-0">
              <div class="info">
                <div class="section-head style-4">
                  <small class="title_small">إدارة أفضل للملاحظات</small>
                  <h2 class="mb-30">ملاحظاتك <span>في امان</span></h2>
                </div>
                <p class="text mb-40">
                  يتزامن تلقائيًا عبر جميع أجهزتك. يمكنك أيضًا الوصول إلى الملاحظات وكتابتها بدون
                  اتصال بالإنترنت.
                </p>
                <div class="faq style-3 style-4">
                  <div class="accordion" id="accordionExample">
                    <div class="accordion-item">
                      <h2 class="accordion-header" id="heading1">
                        <button
                          class="accordion-button"
                          type="button"
                          data-bs-toggle="collapse"
                          data-bs-target="#collapse1"
                          aria-expanded="true"
                          aria-controls="collapse1"
                        >
                          إنشاء وحفظ الملاحظات الخاصة بك مع الوسائط المتعددة
                        </button>
                      </h2>
                      <div
                        id="collapse1"
                        class="accordion-collapse collapse show"
                        aria-labelledby="heading1"
                        data-bs-parent="#accordionExample"
                      >
                        <div class="accordion-body">
                          يتم دعم الصور ومقاطع الفيديو وملفات PDF والملفات الصوتية. قم بإنشاء
                          تعبيرات رياضية ومخططات مباشرة من التطبيق. التقط صورًا باستخدام تطبيق
                          الهاتف المحمول واحفظها في ملاحظة.
                        </div>
                      </div>
                    </div>
                    <div class="accordion-item">
                      <h2 class="accordion-header" id="heading2">
                        <button
                          class="accordion-button collapsed"
                          type="button"
                          data-bs-toggle="collapse"
                          data-bs-target="#collapse2"
                          aria-expanded="false"
                          aria-controls="collapse2"
                        >
                          ملحق Web Clipper
                        </button>
                      </h2>
                      <div
                        id="collapse2"
                        class="accordion-collapse collapse"
                        aria-labelledby="heading2"
                        data-bs-parent="#accordionExample"
                      >
                        <div class="accordion-body">
                          يتم دعم الصور ومقاطع الفيديو وملفات PDF والملفات الصوتية. قم بإنشاء
                          تعبيرات رياضية ومخططات مباشرة من التطبيق. التقط صورًا باستخدام تطبيق
                          الهاتف المحمول واحفظها في ملاحظة.
                        </div>
                      </div>
                    </div>
                    <div class="accordion-item">
                      <h2 class="accordion-header" id="heading3">
                        <button
                          class="accordion-button collapsed"
                          type="button"
                          data-bs-toggle="collapse"
                          data-bs-target="#collapse3"
                          aria-expanded="false"
                          aria-controls="collapse3"
                        >
                          حماية ملاحظتك مع القفل
                        </button>
                      </h2>
                      <div
                        id="collapse3"
                        class="accordion-collapse collapse"
                        aria-labelledby="heading3"
                        data-bs-parent="#accordionExample"
                      >
                        <div class="accordion-body">
                          يتم دعم الصور ومقاطع الفيديو وملفات PDF والملفات الصوتية. قم بإنشاء
                          تعبيرات رياضية ومخططات مباشرة من التطبيق. التقط صورًا باستخدام تطبيق
                          الهاتف المحمول واحفظها في ملاحظة.
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <a
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
                </a>
              </div>
            </div>
            <div class="col-lg-6 order-0 order-lg-2">
              <div class="img mb-30 mb-lg-0">
                <img src="/assets/img/about/2mobiles.png" alt="" />
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
                <img src="/assets/img/about/about_s4_img3.png" alt="" />
              </div>
            </div>
            <div class="col-lg-5">
              <div class="info">
                <div class="section-head style-4">
                  <small class="title_small">ثيمات جميلة</small>
                  <h2 class="mb-30">ركز أكثر مع <span>المظهر الداكن</span></h2>
                </div>
                <p class="text mb-40">
                  قم بتطبيق سمات نوتيرو الأنيقة حسب ذوقك. تعمل السمات المظلمة بشكل ممتاز لأولئك
                  الذين يفضلون الوضع الخالي من الإلهاء.
                </p>
                <ul>
                  <li class="d-flex align-items-center op-4">
                    <i class="bi bi-dot fs-2 me-2 lh-1 color-blue4"></i>
                    <h6 class="fw-bold">تصفية الملاحظات باستخدام الكلمات الرئيسية المتطابقة</h6>
                  </li>
                  <li class="d-flex align-items-center">
                    <i class="bi bi-dot fs-2 me-2 lh-1 color-blue4"></i>
                    <h6 class="fw-bold">8 موضوعات جميلة لتختارها</h6>
                  </li>
                  <li class="d-flex align-items-center op-4">
                    <i class="bi bi-dot fs-2 me-2 lh-1 color-blue4"></i>
                    <h6 class="fw-bold">وفر الطاقة لجهازك</h6>
                  </li>
                  <li class="d-flex align-items-center op-4">
                    <i class="bi bi-dot fs-2 me-2 lh-1 color-blue4"></i>
                    <h6 class="fw-bold">من السهل التبديل بين الوضع الفاتح والداكن</h6>
                  </li>
                </ul>
                <a
                  href="/page-services-5"
                  class="btn rounded-pill bg-blue4 fw-bold text-white mt-50"
                >
                  <small>اكتشف الآن</small>
                </a>
              </div>
            </div>
          </div>
        </div>
        <img src="/assets/img/about/about_s4_bubble.png" alt="" class="bubble" />
      </div>

      <div class="integration pt-60" data-scroll-index="3">
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
            <div class="swiper-slide" v-for="n in 5" :key="n">
              <div class="img">
                <img :src="`/assets/img/screenshots/${n}.${n === 3 ? 'jpg' : 'png'}`" alt="" />
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
                <small class="title_small">اراء العملاء</small>
                <h2 class="mb-30">محبوب من <span>العملاء</span></h2>
              </div>
              <p class="text mb-40">
                أحب نوتيرو من آلاف العملاء في جميع أنحاء العالم وحصل على الثقة من الشركات الكبرى.
              </p>
              <div class="numbs">
                <div class="num-card">
                  <div class="icon img-contain">
                    <img src="/assets/img/icons/testi_s4_ic1.png" alt="" />
                  </div>
                  <h2>2,5M+</h2>
                  <p>
                    تحميل و <br />
                    تثبيت
                  </p>
                </div>
                <div class="num-card">
                  <div class="icon img-contain">
                    <img src="/assets/img/icons/testi_s4_ic2.png" alt="" />
                  </div>
                  <h2>4.8/5</h2>
                  <div class="stars">
                    <i class="fas fa-star" v-for="n in 5" :key="n"></i>
                  </div>
                  <p>بناءاً على هذا العدد من التقييمات 1،258</p>
                </div>
              </div>
              <div class="d-flex align-items-center mt-70">
                <a
                  href="https://www.apple.com/app-store/"
                  class="btn rounded-pill bg-blue4 fw-bold text-white me-4"
                  target="_blank"
                >
                  <small>انظر التعليقات على متجر التطبيقات</small>
                </a>
                <a href="https://youtu.be/pGbIOC83-So?t=21" data-lity class="play-btn">
                  <span class="icon me-2"><i class="fas fa-play ms-1"></i></span>
                  <strong class="small"
                    >مشاهده <br />
                    البرومو</strong
                  >
                </a>
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
          <small class="title_small">خطة الاسعار</small>
          <h2 class="mb-30">ابدأ بـ <span>سعر مناسب</span></h2>
        </div>
        <div class="content">
          <div class="toggle_switch d-flex align-items-center justify-content-center mb-40">
            <div class="form-check form-switch p-0">
              <label class="form-check-label" for="flexSwitchCheckDefault"
                ><small>تدفع شهريا</small></label
              >
              <input
                class="form-check-input float-none bg-blue4"
                type="checkbox"
                id="flexSwitchCheckDefault"
                checked
              />
              <label class="form-check-label" for="flexSwitchCheckDefault"
                ><small>دفع سنوى</small></label
              >
            </div>
          </div>
          <div class="row gx-0">
            <div class="col-lg-6">
              <div class="price-card">
                <div class="price-header pb-4">
                  <h6>
                    <img src="/assets/img/icons/price_s4_1.png" alt="" class="icon" /> الخطة
                    الأساسية
                  </h6>
                  <h2>مجانا <small>/ شهري</small></h2>
                  <p>نسخة تجريبية مجانية لمدة 14 يومًا، يمكنك استخدام أكثر من 20 ميزة أساسية</p>
                </div>
                <div class="price-body py-4">
                  <ul>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="far fa-sticky-note"></i>
                      </small>
                      <p class="fw-bold">اكتب 5 ملاحظات على iOS و Android فقط</p>
                    </li>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-paperclip"></i>
                      </small>
                      <p class="fw-bold">أضف المرفقات والجداول والأكواد والمزيد إلى ملاحظاتك</p>
                    </li>
                    <li class="d-flex align-items-center mb-3 op-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-lock"></i>
                      </small>
                      <p class="fw-bold">
                        حماية الملاحظات وأجهزة الكمبيوتر المحمولة الخاصة بك مع قفل
                      </p>
                    </li>
                    <li class="d-flex align-items-center mb-3 op-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-undo"></i>
                      </small>
                      <p class="fw-bold">وضع التركيز والمظهر الداكن</p>
                    </li>
                    <li class="d-flex align-items-center op-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-download"></i>
                      </small>
                      <p class="fw-bold">تصدير إلى تنسيقات Text و PDF و HTML و Markdown</p>
                    </li>
                  </ul>
                  <a
                    href="/page-contact-5"
                    class="btn rounded-pill hover-blue4 fw-bold mt-50 px-5 border-blue4"
                  >
                    <small>سجل الان</small>
                  </a>
                </div>
              </div>
            </div>
            <div class="col-lg-6">
              <div class="price-card">
                <div class="price-header pb-4">
                  <h6>
                    <img src="/assets/img/icons/price_s4_2.png" alt="" class="icon" /> خطة متميزة
                  </h6>
                  <h2>$29 <small>/ شهري</small></h2>
                  <p>جرب جميع الميزات المتميزة والدفع لمرة واحدة فقط</p>
                </div>
                <div class="price-body py-4">
                  <ul>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="far fa-sticky-note"></i>
                      </small>
                      <p class="fw-bold">اكتب 5 ملاحظات على iOS و Android فقط</p>
                    </li>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-paperclip"></i>
                      </small>
                      <p class="fw-bold">أضف المرفقات والجداول والأكواد والمزيد إلى ملاحظاتك</p>
                    </li>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-lock"></i>
                      </small>
                      <p class="fw-bold">
                        حماية الملاحظات وأجهزة الكمبيوتر المحمولة الخاصة بك مع قفل
                      </p>
                    </li>
                    <li class="d-flex align-items-center mb-3">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-undo"></i>
                      </small>
                      <p class="fw-bold">وضع التركيز والمظهر الداكن</p>
                    </li>
                    <li class="d-flex align-items-center">
                      <small
                        class="icon-30 bg-blue4 rounded-circle text-white d-inline-flex align-items-center justify-content-center me-3 flex-shrink-0"
                      >
                        <i class="fas fa-download"></i>
                      </small>
                      <p class="fw-bold">تصدير إلى تنسيقات Text و PDF و HTML و Markdown</p>
                    </li>
                  </ul>
                  <a
                    href="/page-contact-5"
                    class="btn rounded-pill bg-blue4 fw-bold text-white px-5 mt-50"
                  >
                    <small>سجل الان</small>
                  </a>
                </div>
                <div class="off">
                  <span
                    >20% <br />
                    خصم</span
                  >
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
                        طراحی و توسعه سامانه یکپارچه مدیریت داده و منابع آب ایران (سیماب) یک سامانه
                        اختصاصی برای شرکت‌های آب منطقه‌ای بوده که تمامی فرآیندهای داده‌برداری،
                        کنترل، نظارت، گزارش‌گیری و تحلیل داده‌های منابع آب را شامل می‌شود. در حال
                        حاضر این سامانه تمامی فرایندهای دفتر مطالعات پایه منابع آب را الکترونیکی
                        نموده است و از سال 1399 در دفتر مطالعات پایه منابع آب شرکت آب منطقه‌ای
                        خراسان رضوی راه‌اندازی شد و به عنوان سامانه اصلی این دفتر در حال کار است.
                        این سامانه هم‌اکنون در دو استان خراسان رضوی و اصفهان فعال است.
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
                        آیا محصولات ثبت اختراع یا گواهی استاندارد دارند؟
                      </button>
                    </h2>
                    <div
                      id="collapse12"
                      class="accordion-collapse collapse show rounded-0"
                      aria-labelledby="heading12"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        سامانه سیماب دارای تاییدیه براساس ارزیابی سافا (سامانه ارزیابی فناوری ایران)
                        حائز بالاترین سطح آمادگی فناوری (TRL9) می‌باشد و همچنین دارای تاییدیه افتا
                        از سازمان فناوری اطلاعات ایران میباشد.
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
                        آیا نرم‌افزار نیاز به اینترنت دائمی دارد یا به صورت آفلاین هم کار می‌کند؟
                      </button>
                    </h2>
                    <div
                      id="collapse13"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading13"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        بله امکان استفاده از سامانه به صورت آفلاین و آنلاین وجود دارد و به دلیل نیاز
                        های سامانه برای استفاده های آفلاین قابلیت استفاده به هر دو صورت امکان پذیر
                        است.
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
                        آیا امکان گزارش‌گیری و خروجی گرفتن در قالب Excel/PDF وجود دارد؟
                      </button>
                    </h2>
                    <div
                      id="collapse4"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading4"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        بله، سامانه این قابلیت را دارد که گزارش‌ها را به‌صورت چارت، جدول و همچنین در
                        قالب فایل‌های Excel و CSV ارائه دهد. این امکان به کاربران کمک می‌کند تا
                        داده‌ها را به‌صورت دقیق تحلیل کرده و در نرم‌افزارهای مختلف مورد استفاده قرار
                        دهند. علاوه بر این، امکان شخصی‌سازی گزارش‌ها بر اساس نیازهای سازمان نیز
                        فراهم شده است.
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
                        كيف تقوم نيترو بتخزين بياناتي?
                      </button>
                    </h2>
                    <div
                      id="collapse5"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading5"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        من خلال التعاون مع العملاء في مناقشة الاحتياجات والطلب، نحن قادرون على تحقيق
                        التفاهم المتبادل، واكتساب ثقة العملاء لتقديم المشورة المناسبة
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
                        لا يدعم نيترو تخزين البيانات على iCloud?
                      </button>
                    </h2>
                    <div
                      id="collapse6"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading6"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        من خلال التعاون مع العملاء في مناقشة الاحتياجات والطلب، نحن قادرون على تحقيق
                        التفاهم المتبادل، واكتساب ثقة العملاء لتقديم المشورة المناسبة
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
                        كيف يمكنني تغيير البريد الإلكتروني أو كلمة المرور الخاصة بي?
                      </button>
                    </h2>
                    <div
                      id="collapse7"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading7"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        من خلال التعاون مع العملاء في مناقشة الاحتياجات والطلب، نحن قادرون على تحقيق
                        التفاهم المتبادل، واكتساب ثقة العملاء لتقديم المشورة المناسبة
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
                        هل يمكن استخدام ترخيص Premium الخاص بي لجميع الأجهزة?
                      </button>
                    </h2>
                    <div
                      id="collapse8"
                      class="accordion-collapse collapse rounded-0"
                      aria-labelledby="heading8"
                      data-bs-parent="#accordionSt4"
                    >
                      <div class="accordion-body">
                        من خلال التعاون مع العملاء في مناقشة الاحتياجات والطلب، نحن قادرون على تحقيق
                        التفاهم المتبادل، واكتساب ثقة العملاء لتقديم المشورة المناسبة
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

    <!-- ====== انجمن ====== -->
    <section class="community section-padding pt-0 style-4">
      <div class="container">
        <div class="section-head text-center style-4">
          <small class="title_small">مجتمع نوتيرو</small>
          <h2 class="mb-30">انضم إلى <span>مركزنا</span></h2>
        </div>
        <div class="content">
          <a href="#" class="commun-card">
            <div class="icon"><i class="fab fa-github"></i></div>
            <div class="inf">
              <h5>جيت هوب</h5>
              <p>المصدر المفتوح ورمز الاتصال</p>
            </div>
          </a>
          <a href="#" class="commun-card">
            <div class="icon"><i class="fab fa-twitter"></i></div>
            <div class="inf">
              <h5>تويتر</h5>
              <p>آخر الأخبار والتحديثات</p>
            </div>
          </a>
          <a href="#" class="commun-card">
            <div class="icon"><i class="fab fa-telegram"></i></div>
            <div class="inf">
              <h5>تليجرام</h5>
              <p>قناه للمجتمع</p>
            </div>
          </a>
        </div>
      </div>
    </section>
  </main>

  <!-- ====== فوتر ====== -->
  <footer class="style-4" data-scroll-index="8">
    <div class="container">
      <div class="section-head text-center style-4">
        <h2 class="mb-10">جاهز <span>للتنزيل</span></h2>
        <p>
          اكتشف مساحاتك المفضلة الجديدة، من ساو باولو إلى سيول. قم بالتنزيل من App Store أو Google
          Play.
        </p>
        <div class="d-flex align-items-center justify-content-center mt-50">
          <a
            href="https://www.apple.com/app-store/"
            class="btn rounded-pill bg-blue4 fw-bold text-white me-4"
            target="_blank"
          >
            <small><i class="fab fa-apple me-2 pe-2 border-end"></i> تنزيل من متجر التطبيقات</small>
          </a>
          <a
            href="https://play.google.com/store/apps"
            class="btn rounded-pill hover-blue4 fw-bold border-blue4"
            target="_blank"
          >
            <small><i class="fab fa-google-play me-2 pe-2 border-end"></i> تنزيل من متجر ابل</small>
          </a>
        </div>
      </div>
      <div class="foot mt-80">
        <div class="row align-items-center">
          <div class="col-lg-2">
            <div class="logo">
              <img src="/assets/img/logo_lgr.png" alt="" />
            </div>
          </div>
          <div class="col-lg-8">
            <ul class="links">
              <li><a href="/" class="active">الرئيسية</a></li>
              <li><a href="/page-about-5">من نحن</a></li>
              <li><a href="/page-product-5">المنتجات</a></li>
              <li><a href="/page-portfolio-5">المشاريع</a></li>
              <li><a href="/page-services-5">الخدمات</a></li>
              <li><a href="/page-shop-5">المتجر</a></li>
              <li><a href="/page-blog-5">الاخبار</a></li>
              <li><a href="/page-contact-5">اتصل بنا</a></li>
            </ul>
          </div>
          <div class="col-lg-2">
            <div class="dropdown">
              <button
                class="icon-25 dropdown-toggle p-0 border-0 bg-transparent rounded-circle img-cover"
                type="button"
                id="dropdownMenuButton1"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                <img src="/assets/img/lang.png" alt="" class="me-2" />
                <small>العربية</small>
              </button>
              <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
                <li><a class="dropdown-item" href="#">English</a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="copywrite text-center">
        <small class="small">
          © 2023 حقوق التأليف والنشر
          <a href="#" class="fw-bold text-decoration-underline">Iteck Co.</a>
          كل الحقوق محفوظة. صمم بواسطة
          <a
            href="https://themeforest.net/user/themescamp"
            class="fw-bold text-decoration-underline"
            >ThemesCamp</a
          >
        </small>
      </div>
    </div>
    <img src="/assets/img/footer/footer_4_wave.png" alt="" class="wave" />
  </footer>

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
</style>
