<template>
   <div class="form">
       <form class="text-center">
          <div>
              <h2 class="text-white">Personal Form</h2>
          </div>
          <div class="mb-4">
              <!-- <label for="name">Nama Lengkap</label> -->
              <input v-model="name" @keypress="checkValue('name')" type="text" class="form-control" id="name" placeholder="Masukkan Nama">
              <small id="error-name" class="form-text text-muted bold" style="color: red !important" v-if="errorName">{{ errorName }}</small>
          </div>
          <div class="mb-4">
              <!-- <label for="address">Alamat</label> -->
              <input v-model="address" @keypress="checkValue('address')" type="text" class="form-control" id="address" placeholder="Alamat Sesuai Ktp">
              <small id="error-address" class="form-text text-muted bold" style="color: red !important" v-if="errorAddress">{{errorAddress}}</small>
          </div>
          <div class="form-group flex-auto send-button">
              <Button
                  data-toggle = 'modal'
                  data-target = '#exampleModal'
                  titleButton = 'Daftar'
                  @click-button = 'submit'
              />
          </div>
          <div v-if= "sendData">
              <Modal
                  @click-reset = 'close'
              />
          </div>
      </form>
  </div>
</template>
<script>
import Button from "~/components/atoms/Button.vue"
import Modal from "~/components/mollecules/Modal.vue"
export default {
  components: {
    Button: Button,
    Modal: Modal,
  },
  data() {
    return {
      sendData: false,
      name: '',
      address: '',
      errorName: '',
      errorAddress: ''
    }
  },
  methods: {
    submit() {
      this.validateInput()
      if (this.name !='' && this.address !='') {
        this.sendData = true
        // alert('terima kasih')
    }
    },
    validateInput() {
      if (this.name == '') {
        this.errorName = 'Nama Belum di Isi'
      }
      if (this.address == '') {
        this.errorAddress = 'Alamat Anda belum di Isi'
      }
    },
    checkValue(param) {
      if (param == 'name') {
        this.errorName = ''
      }
      if (param == 'address') {
        this.errorAddress = ''
      }
    },
    close() {
      this.name = ''
      this.address = ''
      this.sendData = ''
    }
  }
}
</script>
<style>
  form{
    background-color: rgb(0, 0, 0,0.3);
    box-shadow: 0px 0px 20px;
    max-width: 350px;
    padding: 80px 20px;
    margin: 0px auto;
    border-radius: 50px 0px 50px 0px;
  }
  .form {
    padding: 80px 0px 155px 750px;
    background-image: url(assets/images/darkPhoto.jpg);
    background-size: cover;
  }
  h2 {
    font-weight: 700;
    margin-bottom: 60px;
  }
  @media(max-width: 900px) {
    .form {
      width: 100%;
      background-size: cover;
      margin: 0px 0px;
      padding: 40px 20px;
      height: 600px;
    }
    form {
      background-color: rgb(0, 0, 0,0.3);
      max-width: 200px;
      padding: 20px 20px;
      margin: 0px auto;
      border-radius: 50px 0px 50px 0px;
    }
    h2 {
      margin-bottom: 20px;
    }
  }
</style>