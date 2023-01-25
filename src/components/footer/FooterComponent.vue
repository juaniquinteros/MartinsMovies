<template>
  <footer class="footer bg-dark" id="footer">
    <div class="footer-widget">
      <div class="container">
        <div class="row">
          <div class="col-lg-3 col-md-6 col-sm-12">
            <div class="about">
              <img
                src="../../assets/logo-white.svg"
                class="app-logo"
                alt="Logotipo"
              />
              <p id="footer-text">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                Itaque, ducimus, atque. Praesentium suscipit provident explicabo
                dignissimos nostrum numquam deserunt earum accusantium et fugit.
              </p>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 col-sm-12">
            <div class="links">
              <h4>Useful Links</h4>
              <ul>
                <li>
                  <a href="#">About Martin's Movies</a>
                </li>
                <li>
                  <a href="#">Blog</a>
                </li>
                <li>
                  <a href="#">Forum</a>
                </li>
                <li>
                  <a href="#">My Acount</a>
                </li>
                <li>
                  <a href="#">Watch list</a>
                </li>
              </ul>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 col-sm-12">
            <div class="blog">
              <h4>Latest News</h4>
              <ul>
                <li>
                  <a href="#">Blog Post 1</a>
                  <p>JANUAR 25, 2023</p>
                </li>
                <li>
                  <a href="#">Blog Post 2</a>
                  <p>JANUAR 25, 2023</p>
                </li>
                <li>
                  <a href="#">Blog Post 3</a>
                  <p>JANUAR 25, 2023</p>
                </li>
              </ul>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 col-sm-12">
            <div class="social">
              <h4>Follow us</h4>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                Itaque, ducimus, atque.
              </p>
              <ul>
                <li>
                  <a href="#" class="btn-social facebook">
                    <div class="btn-social-icon">
                      <i class="fa-brands fa-facebook-f"></i>
                    </div>
                  </a>
                </li>
                <li>
                  <a href="#" class="btn-social twitter">
                    <div class="btn-social-icon">
                      <i class="fa-brands fa-twitter"></i>
                    </div>
                  </a>
                </li>
                <li>
                  <a href="#" class="btn-social google">
                    <div class="btn-social-icon">
                      <i class="fa-brands fa-google-plus-g"></i>
                    </div>
                  </a>
                </li>
                <li>
                  <a href="#" class="btn-social instagram">
                    <div class="btn-social-icon">
                      <i class="fa-brands fa-instagram"></i>
                    </div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-copyright">
      <div class="container">
        <div class="row">
          <div class="links col-lg-6 col-md-12">
            <ul>
              <li><a href="#"> Privacy & Cookies</a></li>
              <li><a href="#">Terms & Conditions</a></li>
              <li><a href="#">Legal Disclaimer</a></li>
              <li><a href="#">Community</a></li>
            </ul>
          </div>
          <div class="copyright col-lg-6 col-md-12">
            <p>
              All Rights Reserved by
              <a href="#">Martin's Movies</a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent",
};
</script>


<style>
.footer.bg-dark {
  color: white;
}

.bg-dark {
  background-color: #3e4555 !important;
}

.footer-widget {
  padding: 100px 0;
}

.footer .about img {
  margin-bottom: 40px;
  height: 28px;
}

.footer .about p {
  margin: 0;
  font-size: 16px;
  line-height: 24px;
}

.footer h4 {
  margin-bottom: 40px;
  text-transform: capitalize;
  font-size: 24px;
}

.footer ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer ul li a {
  text-transform: capitalize;
  text-decoration: none;
  padding-bottom: 10px;
  color: white;
  transition: all 0.3s ease;
}

.footer .footer-widget .links ul li a:hover {
  color: #9352b3;
  padding-left: 10px;
}

.footer .footer-widget .blog ul li a:hover {
  color: #9352b3;
}

.footer .footer-widget .blog ul li:first-child {
  padding-top: 0;
}

.footer .footer-widget .blog ul li {
  padding: 10px 0;
}

.footer .footer-widget .blog ul li p {
  color: #a8a1ac;
  text-transform: uppercase;
  font-weight: 500;
  font-size: 13px;
  margin-bottom: 0;
}

.footer .footer-widget .social ul li {
  display: inline-block;
  padding: 0 5px;
}

.footer .footer-widget .social ul li:first-child {
  padding-left: 0;
}

.btn-social {
  color: white;
  border: 1px solid #4d5154;
  display: block;
  border-radius: 50%;
  overflow: hidden;
  width: 35px;
  height: 35px;
  transition: 0.3s ease;
}

.btn-social-icon {
  color: white;
  text-align: center;
  line-height: 35px;
}

.btn-social.facebook:hover {
  background-color: #3b5998;
}

.btn-social.twitter:hover {
  background-color: #4cc4f2;
}

.btn-social.google:hover {
  background-color: #dd4b39;
}

.btn-social.instagram:hover {
  background-color: #9b6954;
}

.footer-copyright{
    border-top: 1px solid rgba(255, 255, 255, .2);
    padding: 30px 0;
}

.footer-copyright .links ul li{
    display: inline-block;
    margin-right: 10px;
    margin-bottom: 5px;
}

.footer-copyright p{
    text-align: right;
}

.footer-copyright p a{
    text-decoration: none;
    color: white;
}

.footer-copyright a:hover{
    color: #9352b3;
}


@media (max-width: 987px){
    .footer-widget .about{
      margin-bottom: 50px;
    }
    .footer-widget .links{
      margin-bottom: 50px;
    }
    .footer-copyright p{
        text-align: center;
    }

    .footer-copyright .links{
        text-align: center;
    }
}
</style>