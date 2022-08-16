<template>
<div class="adjust">
     <form @submit="onSubmit" class="form">
      <div class="title">Grocery</div>
      <div class="subtitle">add it to your list</div>
      <div class="input-container ic1">
        <input id="firstname" class="input" v-model="text"  type="text" placeholder=" " />
        <div class="cut"></div>
        <label for="firstname" class="placeholder">Grocery</label>
      </div>
      <div class="input-container ic2">
        <input id="lastname" class="input" type="text" placeholder=" "   v-model="store"/>
        <div class="cut"></div>
        <label for="lastname" class="placeholder">Store?</label>
      </div>
      <br />
      <div class="item">
      <div class="checkbox-rect2">
        <input type="checkbox" id="checkbox-rect2" v-model="reminder" name="check">
        <label for="checkbox-rect2">Set Reminder</label>
      </div>
      </div>
      <div >
    <button class="button-3"> Add grocery</button>
    </div>
    </form>
</div>
</template>

<script>

export default {
    name: 'AddGrocery',
    data() {
        return {
            text: '',
        store: '',
        reminder:false
    }
    },
    methods: {
      onSubmit(e){
        e.preventDefault()

        if(!this.text) {
        alert('please add a grocery')
        if(!this.store) {
        alert('please add a store where you want to get the grocery from')
        }
        return
        }

        const newList = {
          text: this.text,
          store: this.store,
          reminder: this.reminder
        }
        
        console.log(newList)
        this.$emit('add-list', newList)

        this.text = ''
        this.store=''
        this.reminder= false
      }
    }
}
</script>

<style scoped>
.item {
  margin-bottom: 1em;
}
.checkbox-rect2 input[type="checkbox"] {
  display: none;
}
.checkbox-rect2 input[type="checkbox"] + label {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 20px;
  font: 14px/20px "Open Sans", Arial, sans-serif;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
}
.checkbox-rect2 input[type="checkbox"]:hover + label:hover {
  color: #ffffff;
}
.checkbox-rect2 input[type="checkbox"]:hover + label:before { 
  border: 1px solid #607E61;
  box-shadow: 2px 1px 0 #ffffff;
}
.checkbox-rect2 input[type="checkbox"] + label:last-child {
  margin-bottom: 0;
}
.checkbox-rect2 input[type="checkbox"] + label:before {
  content: "";
  display: block;
  width: 1.4em;
  height: 1.4em;
  border: 1px solid #ffffff;
  border-radius: 0.2em;
  position: absolute;
  left: 0;
  top: 0;
  -webkit-transition: all 0.2s, background 0.2s ease-in-out;
  transition: all 0.2s, background 0.2s ease-in-out;
  background: 607E61;
  box-shadow: -2px -1px 0 #ffffff;
  background: #f3f3f3;
}
.checkbox-rect2 input[type="checkbox"]:checked + label:before {
  border: 2px solid #fff;
  border-radius: 0.3em;
  background: #607E61;
  box-shadow: 2px 1px 0 #607E61;
}
body {
  align-items: center;
  background-color: #000;
  display: flex;
  align-content: center;
  justify-content: center;
  height: 50vh;
}

.form {
  background-color: #607E61 ;
  border-radius: 20px;
  box-sizing: border-box;
  height: 400px;
  padding: 20px;
  width: 320px;
  display:inline-block;
}

.title {
  color: #eee;
  font-family: sans-serif;
  font-size: 36px;
  font-weight: 600;
  margin-top: 30px;
}

.subtitle {
  color: #eee;
  font-family: sans-serif;
  font-size: 16px;
  font-weight: 600;
  margin-top: 10px;
}

.input-container {
  height: 50px;
  position: relative;
  width: 100%;
}

.ic1 {
  margin-top: 40px;
}

.ic2 {
  margin-top: 30px;
}

.input {
  background-color: #ffffff;
  border-radius: 12px;
  border: 0;
  box-sizing: border-box;
  color: #000000;
  font-size: 18px;
  height: 100%;
  outline: 0;
  padding: 4px 20px 0;
  width: 100%;
}

.cut {
  background-color: #607E61;
  border-radius: 10px;
  height: 20px;
  left: 20px;
  position: absolute;
  top: -20px;
  transform: translateY(0);
  transition: transform 200ms;
  width: 76px;
}

.cut-short {
  width: 50px;
}

.input:focus ~ .cut,
.input:not(:placeholder-shown) ~ .cut {
  transform: translateY(8px);
}

.placeholder {
  color: #65657b;
  font-family: sans-serif;
  left: 20px;
  line-height: 14px;
  pointer-events: none;
  position: absolute;
  transform-origin: 0 50%;
  transition: transform 200ms, color 200ms;
  top: 20px;
}

.input:focus ~ .placeholder,
.input:not(:placeholder-shown) ~ .placeholder {
  transform: translateY(-30px) translateX(10px) scale(0.75);
}

.input:not(:placeholder-shown) ~ .placeholder {
  color: #ffffff;
}

.input:focus ~ .placeholder {
  color: #FFFFFF;
}

.button-3 {
  appearance: none;
  background-color: #3c7a4e;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-3:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-3:hover {
  background-color: #39834e;
}

.button-3:focus {
  box-shadow: rgba(49, 138, 74, 0.4) 0 0 0 3px;
  outline: none;
}

.button-3:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-3:active {
  background-color: #298e46;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}
</style>