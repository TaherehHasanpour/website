<template>
  <footer class="style-4" data-scroll-index="8">
    <div class="container">
      <!-- Company Info -->
      <!-- <div class="section-head text-center style-4">
        <h2 class="mb-10">پایدار تجهیز <span>آتی خراسان</span></h2>

        <p>
          شرکت دانش‌بنیان و فناور پایدار تجهیز آتی خراسان در پارک علم و فناوری خراسان مستقر است.
        </p>
      </div> -->

      <!-- Footer Main -->
      <div class="foot mt-20">
        <div class="row align-items-start">
          <!-- Logo + Company -->
          <div class="col-lg-4 col-md-6">
            <div class="footer-company">
              <div class="logo mb-20">
                <img src="/assets/img/logos/atey_logo.png" alt="" />
              </div>

              <h5>پایدار تجهیز آتی خراسان</h5>

              <div class="company-badge">دانش‌بنیان - فناور</div>

              <div class="company-info mt-20">
                <div class="info-item">
                  <img
                    width="20px"
                    height="20px"
                    src="/public/assets/img/icons/svg/location-dot.svg"
                    alt=""
                  />
                  <span>مشهد، پارک علم و فناوری خراسان</span>
                </div>

                <div class="info-item">
                  <i class="icofont-building"></i>
                  <span>ساختمان دانش‌بنیان، واحد 415</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Useful Links -->
          <div class="col-lg-4 col-md-6">
            <div class="footer-links">
              <h5 class="footer-title">محصولات نرم افزاری</h5>

              <ul>
                <li>
                  <a href="https://simmab.ir/" target="_blank" rel="noopener noreferrer">
                    سیــــماب
                  </a>
                </li>

                <li>
                  <a href="https://gashtab.ir/" target="_blank" rel="noopener noreferrer">
                    گشتــــاب
                  </a>
                </li>

                <li>
                  <a href="#" target="_blank" rel="noopener noreferrer"> آبـــان </a>
                </li>
              </ul>
            </div>
          </div>

          <!-- Contact -->
          <div class="col-lg-4 col-md-6">
            <div class="footer-contact">
              <h5 class="footer-title">ارتباط با ما</h5>

              <div class="contact-item">
                <img
                  width="20px"
                  height="20px"
                  src="/public/assets/img/icons/svg/envelope.svg"
                  alt=""
                />

                <div>
                  <small>پست الکترونیکی</small>
                  <a href="mailto:info@atey.ir"> info@atey.ir </a>
                </div>
              </div>

              <div class="contact-item">
                <img
                  width="20px"
                  height="20px"
                  src="/public/assets/img/icons/svg/phone.svg"
                  alt=""
                />

                <div>
                  <small>تلفن تماس</small>
                  <a href="tel:05135419795"> 05135419795 </a>
                </div>
              </div>

              <!-- Social Media -->
              <div class="footer-social mt-25">
                <a href="https://atey.ir" target="_blank" rel="noopener noreferrer" title="وب‌سایت">
                  <img
                    width="20px"
                    height="20px"
                    src="/public/assets/img/icons/svg/internet-explorer.svg"
                    alt=""
                  />
                </a>

                <a href="#" target="_blank" rel="noopener noreferrer" title="تلگرام">
                  <img
                    width="20px"
                    height="20px"
                    src="/public/assets/img/icons/svg/telegram.svg"
                    alt=""
                  />
                </a>

                <a
                  href="https://instagram.com/atey.ir"
                  target="_blank"
                  rel="noopener noreferrer"
                  title="اینستاگرام"
                >
                  <img
                    width="20px"
                    height="20px"
                    src="/public/assets/img/icons/svg/instagram.svg"
                    alt=""
                  />
                </a>

                <a href="tel:05135419795" title="توییتر">
                  <img width="20px" height="20px" src="/public/assets/img/icons/svg/x.svg" alt="" />
                </a>
                <a href="tel:05135419795" title="لینکدین">
                  <img width="20px" height="20px" src="/public/assets/img/icons/svg/x.svg" alt="" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Copyright -->
      <div class="copywrite text-center">
        <small class="small">
          تمامی حقوق این سامانه متعلق به
          <strong> پایدار تجهیز آتی خراسان </strong>
          می‌باشد ©
        </small>
      </div>
    </div>

    <!-- Wave -->
    <!-- <img src="/assets/img/footer/footer_4_wave.png" alt="" class="wave" /> -->
  </footer>
</template>
<style lang="css">
.style-4 .footer-company {
  text-align: right;
}

.style-4 .footer-company .logo img {
  max-width: 150px;
  max-height: 70px;
  object-fit: contain;
}

.style-4 .footer-company h5 {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 8px;
}

.style-4 .company-badge {
  display: inline-block;
  font-size: 12px;
  padding: 4px 12px;
  border-radius: 20px;
  background: rgba(0, 180, 216, 0.1);
  color: #01305a;
  margin-bottom: 15px;
}

.style-4 .company-info {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.style-4 .info-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
}

.style-4 .info-item i {
  font-size: 17px;
  color: #01305a;
}

/* Footer titles */

.style-4 .footer-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 20px;
}

/* Useful links */

.style-4 .footer-links ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

.style-4 .footer-links li {
  margin-bottom: 11px;
}

.style-4 .footer-links li a {
  font-size: 13px;
  transition: 0.3s;
}

.style-4 .footer-links li a:hover {
  color: #01305a;
  padding-right: 5px;
}

/* Contact */

.style-4 .contact-item {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 15px;
}

.style-4 .contact-item > i {
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: rgba(0, 180, 216, 0.1);
  color: #01305a;
  font-size: 18px;
}

.style-4 .contact-item small {
  display: block;
  font-size: 11px;
  opacity: 0.7;
  margin-bottom: 2px;
}

.style-4 .contact-item a {
  font-size: 13px;
}

/* Social */

.style-4 .footer-social {
  display: flex;
  gap: 9px;
}

.style-4 .footer-social a {
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  border: 1px solid rgba(0, 180, 216, 0.25);
  transition: 0.3s;
}

.style-4 .footer-social a i {
  font-size: 17px;
}

.style-4 .footer-social a:hover {
  background: #01305a;
  color: #fff;
}

/* Copyright */

.style-4 .copywrite {
  border-top: 1px solid rgba(0, 0, 0, 0.08);
  /* margin-top: 50px; */
  padding: 20px 0 25px;
}

.style-4 .copywrite small {
  font-size: 11px;
}

.style-4 .copywrite strong {
  color: #01305a;
}
/* Mobile */
@media (max-width: 991.98px) {
  .style-4 .footer-company,
  .style-4 .footer-links,
  .style-4 .footer-contact {
    text-align: center;
  }

  .style-4 .footer-company .logo {
    /* display: flex;
    justify-content: center; */
    width: 100%;
  }

  .style-4 .company-info {
    align-items: center;
  }

  .style-4 .info-item {
    justify-content: center;
  }

  .style-4 .footer-links ul {
    text-align: center;
  }

  .style-4 .footer-links li {
    margin-bottom: 10px;
  }

  .style-4 .contact-item {
    justify-content: center;
  }

  .style-4 .footer-social {
    justify-content: center;
  }

  .style-4 .footer-title {
    text-align: center;
    padding: 10px;
    margin: 0;
  }

  .style-4 .foot {
    margin-top: 40px !important;
  }
}
</style>
