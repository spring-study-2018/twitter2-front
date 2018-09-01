<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">

          <div class="modal-header">
            <slot name="header">
              <img src="@/assets/default-user.png"/>
              <span>{{tweet.userName}}</span>
               <button class="modal-close-button" @click="$emit('close')">
                X
              </button>
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body">
              <div class="tweet-content">
                {{tweet.content}}
              </div>
            </slot>
          </div>

          <div class="modal-footer">
            <slot name="footer">
              
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'timeline-detail',
  props: ['tweet']
}
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: inline-block;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: inline-block;
  position: relative;
  top:150px;
}

.modal-container {
  width: 640px;
  text-align: center;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header {
  text-align: left;
}

.modal-header img { width:28px} 
.modal-header span { padding-left:20px;position:relative;top:-7px;font-weight: bold} 

.modal-body {
  padding: 20px 0;
}

.modal-default-button {
  float: right;

}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
.modal-close-button {
  background: #fff;
  border:none;
  color:#a1a1a1;
  float:right;
  cursor: pointer;
}
.tweet-content{
  text-align: left;
}
</style>
