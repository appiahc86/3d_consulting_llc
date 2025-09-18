<script setup>
import emailjs from '@emailjs/browser';
import {ref} from "vue";
const sendingMail = ref(false);

const myForm = ref();
const email = ref('');
const sendMail = async () => {
  try {
    if (!email.value.match(/^([\w-\.]+@([\w-]+\.)+[\w-]{2,4})?$/)){
      return alert('Please Enter a valid email address');
    }
    sendingMail.value = true;
    await emailjs.sendForm('service_qgk4sf7', 'template_vnv1ayf', myForm.value, '-q7ENivHmSIyCk0ZV');
    myForm.value.reset();
    alert('Your Message has been sent');
  }catch (e){
    alert('Sorry, error occurred. Please try again later');
  }finally { sendingMail.value = false; }

}
</script>

<template>
  <!-- Contact Start -->
  <div class="container-fluid py-5 mt-5">
    <div class="row">
      <div class="text-center mx-auto pb-5 wow fadeIn" data-wow-delay=".3s" style="max-width: 600px;">
        <h5 class="text-muted">Get In Touch</h5>
        <h1 class="mb-3">Connect with our experts.
        </h1>
<!--        <p class="mb-2">The contact form is currently inactive. Get a functional and working contact form with Ajax & PHP in a few minutes. Just copy and paste the files, add a little code and you're done. <a href="https://htmlcodex.com/contact-form">Download Now</a>.</p>-->
      </div>
    </div>


        <div class="row g-5 mb-5 justify-content-center">
          <div class="col-xl-4 col-lg-6 wow fadeIn" data-wow-delay=".3s">
            <div class="d-flex bg-light p-3 rounded">
              <div class="flex-shrink-0 btn-square navbar-teal rounded-circle" style="width: 64px; height: 64px;">
                <i class="fas fa-map-marker-alt text-white"></i>
              </div>
              <div class="ms-3">
                <h4 class="text-primary">Address</h4>
                <a class="h5">1127 W Main street
                  Jefferson city mo</a>
              </div>
            </div>
          </div>
          <div class="col-xl-4 col-lg-6 wow fadeIn" data-wow-delay=".5s">
            <div class="d-flex bg-light p-3 rounded">
              <div class="flex-shrink-0 btn-square navbar-teal rounded-circle" style="width: 64px; height: 64px;">
                <i class="fa fa-phone text-white"></i>
              </div>
              <div class="ms-3">
                <h4 class="text-primary">Call Us</h4>
                <a class="h5" href="tel:+15514145036">551-414-5036</a>
              </div>
            </div>
          </div>
          <div class="col-xl-4 col-lg-6 wow fadeIn" data-wow-delay=".7s">
            <div class="d-flex bg-light p-3 rounded">
              <div class="flex-shrink-0 btn-square navbar-teal rounded-circle" style="width: 64px; height: 64px;">
                <i class="fa fa-envelope text-white"></i>
              </div>
              <div class="ms-3">
                <h4 class="text-primary">Email Us</h4>
                <a class="h5" href="mailto:info@3dconsultingllc.org" target="_blank">info@3dconsultingllc.org</a>
              </div>
            </div>
          </div>
        </div>


    <div class="row my-4">

      <div class="col-lg-8 wow fadeIn" data-wow-delay=".3s">
          <iframe class="w-100 h-100" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d51093679.562558554!2d-166.01440429687497!3d38.591113776147445!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x87db5eff17447011%3A0xeb92ea7c41a26951!2s1127%20W%20Main%20St%2C%20Jefferson%20City%2C%20MO%2065109%2C%20USA!5e0!3m2!1sen!2sgh!4v1758229485784!5m2!1sen!2sgh" height="300" style="width: auto;"></iframe>
      </div>

      <div class="col-lg-4 wow fadeIn" data-wow-delay=".5s">
        <h3>Contact Form</h3>
        <form class="mb-5" ref="myForm" @submit.prevent="sendMail">
          <div class="form-floating">
            <div class="p-inputgroup">
              <input type="text" placeholder="Your Name*" required class="form-control shadow-non mb-3" name="name">

            </div>
            <div class="p-inputgroup">
              <input type="email" v-model="email" required placeholder="Email*" class="form-control shadow-non mb-3" name="email">
            </div>
            <div class="p-inputgroup">
              <input type="text" required placeholder="Subject*" class="form-control shadow-non mb-3" name="subject">
            </div>
            <div class="p-inputgroup">
              <textarea cols="10" rows="5" required placeholder="Message*" class="form-control shadow-none" name="message"></textarea>
            </div>
            <div class="p-inputgroup mt-3">

              <button type="submit" :disabled="sendingMail" class="btn btn-teal mx-auto mt-3 border-0">
                {{ sendingMail ? 'Please wait..' : 'Send Now' }}
              </button>
            </div>
          </div>
        </form>
      </div>

    </div>





  </div>
  <!-- Contact End -->

</template>

<style scoped>

</style>