<template>
  <div class="container">
    <h2>Account Settings</h2>
    <div class="account" id="account">
      <div class="account__left">
        <div class="account__left-about">
          <img  src="./assets/WIN_20230622_23_09_33_Pro.jpg">
          <h3> {{username}} </h3>
        </div>
        <div class="account__left-choose">
          <button>Account</button>
          <button>Password</button>
          <button>Security</button>
          <button>Application</button>
          <button>Notification</button>
        </div>
      </div>
      <div class="account__right">
        <h3>Account Settings</h3>
        <div class="account__right-info">
          <div class="account__right-row">
            <div class="account__right-column">
              <h4>First Name</h4>
              <input type="text" v-model="name" required>
            </div>
            <div class="account__right-column">
              <h4>Last Name</h4>
              <input type="text" v-model="surname" required>
            </div>
          </div>
          <div class="account__right-row">
            <div class="account__right-column">
              <h4>Email</h4>
              <input type="email" v-model="email" required>
            </div>
            <div class="account__right-column">
              <h4>Phone Number</h4>
              <input type="tel" v-model="phone" required>
            </div>
          </div>
          <div class="account__right-row">
            <div class="account__right-column">
              <h4>Company</h4>
              <input type="text" v-model="company" required>
            </div>
            <div class="account__right-column">
              <h4>Designation</h4>
              <input type="text" v-model="designation" required>
            </div>
          </div>
        </div>
        <div class="account__right-bio">
          <h4>Bio</h4>
          <textarea></textarea>
        </div>
        <div class="account__right-button">
          <div class="first">
            <button v-on:click="update">Update</button>
          </div>
          <div class="second">
            <button v-on:click="cancel">Cancel</button>
          </div>
          <h4>{{ change }}</h4>
        </div> 
      </div>
    </div>
  </div>
</template>

<script>
export default{
  data(){
    return{
      username: 'Aimat Kulmakhan',
      name:'',
      surname:'',
      change:'',
      phone:'',
      company:'',
      designation:''
    }
  },
  methods:{
    update(){
      if(this.name != '' && this.surname != '' && this.phone != '' && this.company != '' && this.designation != ''){
        this.username = this.name + " " + this.surname,
        this.name = '',
        this.surname = '',
        this.change = "changed succefully!"
      }
      else{
        this.change = "please fill all of these blanks"
      }
    },
    cancel(){
      this.name = '',
      this.surname = '',
      this.phone = '',
      this.company = '',
      this.designation = '',
      this.change = ''
    }
  }
};
</script>

<style scoped>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .container{
    display: grid;
    justify-content: center;
    margin-top: 2vh;
  }
  .account{
    margin-top: 2vh;
    padding-right: 10vh;
    padding-left: 10vh;
    padding-top: 5vh; 
    padding-bottom: 5vh;
    display: flex;
    gap:10vh;
    border: 1px solid;
    background-color:#121212;
    border-radius: 10px;
  }
  .account__left-about{
    display: grid;
    justify-content: center;
    justify-items: center;
  }
  .account__left-about img{
    border-radius: 50%;
    width: 100px;
    transition: 0.3s;
  }
  .account__left-about img:hover{
    opacity: 0.5;
    transition: 0.3s;
  }
  .account__left-about h3{
    padding-top: 15px;
  }
  .account__left-choose{
    display: grid;
    padding-top:20px;
  }
  .account__left-choose button{
    padding: 15px;
    background:none;
    border: none;
    font-size: 14px;
    color: rgba(235, 235, 235, 0.64);
    transition: 0.2s;
  }
  .account__left-choose button:hover{
    color: rgba(235, 235, 235);
    transition: 0.2s;
  }
  .account__right{
    border-left: 1px solid;
    padding-left: 10vh;
    padding-right: 1vh;
    padding-top: 1vh;
  }
  .account__right-row{
    padding-top: 20px;
    display: flex;
    gap: 20vh;
  }
  .account__right-column{
    display: block;
  }
  .account__right-column input{
    padding: 7px;
    width: 35vh;
    background-color: #222222;
    /* outline: none; */
    border-radius: 10px;
    border: none;
    color:rgba(235, 235, 235, 0.64);
  }
  .account__right-column h4{
    padding-left: 5px;
    padding-bottom: 7px;
  }
  .account__right-bio{
    padding-top: 20px;
  }
  .account__right-bio textarea{
    padding: 5px;
    background-color: #222222;
    color: rgba(235, 235, 235, 0.64);
    resize: none;
    width: 50vh;
    height: 10vh;
    border: none;
    border-radius: 10px;
  }
  .account__right-bio h4{
    padding-left: 5px;
    padding-bottom: 7px;
  }
  .account__right-button{
    padding-top: 30px;
    display: flex;
    gap:10px;
  }
  .account__right-button button{
    padding: 8px 15px;
    border-radius: 10px;
    border: none;
  }
  .first button{
    background-color: rgba(235, 235, 235, 0.64);
    color: #121212e7;
    transition: 0.3s;
  }
  .first button:hover{
    background-color: rgba(235, 235, 235);
    color: #121212;
    transition: 0.3s;
  }
  .second button{
    background-color: rgba(188, 26, 26, 0.63);
    color: rgba(235, 235, 235, 0.64);
    transition: 0.3s;
  }
  .second button:hover{
    background-color: rgba(188, 26, 26);
    color:rgba(235, 235, 235);
    transition: 0.3s;
  }
  .third{
    padding: 3px;
  }
</style>
