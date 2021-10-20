<template>
<div class="header">
  <br>
  <h3><b> Ovdje možete poslati upit u vezi Crypto Aplikacije </b> </h3>
  <p>Molim ispunite kontakt formu</p>
</div>
<div class="form">
  <form class="form-group" @submit.prevent="sendEmail">
    <label>Name</label>
    <input type="text" class="form-control"  name="name" placeholder="Enter your Name" required >
    <br>
    <label>Email</label>
    <input type="email" class="form-control" name="email" placeholder="Enter your E-mail" required >
    <br>
    <label>Message</label>
    <textarea name="message" class="form-control" placeholder="Your Message" required ></textarea>
    <br>
    <input type="submit" class="btn btn-primary" value="Send">
  </form>
</div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  methods: {
    sendEmail: (e) => {
      emailjs.sendForm('service_ssmtlk4', 'template_u1zpxpd', e.target, 'user_0dzsAVNqopgRXQi4bV2cQ')
        .then((result) => {
            console.log('SUCCESS!', result.status, result.text);
            alert("Email Sent !");
        }, (error) => {
            console.log('FAILED...', error);
            alert("Email Failed!");
        });
    }
  }
}
</script>


<style scoped>
.form{
  text-align: left;
  width:985px; 
  margin:0 auto ;
  padding: 16px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;
}
.btn-primary
{
background-color: #4CAF50;
}

</style>
