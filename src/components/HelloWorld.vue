<template>
  <div>
    <h1>{{ msg }}</h1>
    <button
      class="button"
      :class="{ error: isError, loading: isDisabled, success: isSuccess }"
      :disabled="isDisabled"
      @click="onSubmit"
    >
      submit
    </button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      isDisabled: false,
      isSuccess: false,
      isError: false,
      btnText: "SUBMIT",
    };
  },
  methods: {
    onSubmit() {
      this.isDisabled = true;
      setTimeout(() => {
        this.isDisabled = false;
        var randomNumber = Math.floor(Math.random() * 10);
        if (randomNumber % 2) {
          this.isSuccess = true;
          this.btnText = "SUCCESS";
        } else {
          this.isError = true;
          this.btnText = "ERROR";
        }
      }, 8000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.button {
  padding: 10px 50px;
  background: #21223e;
  border: #21223e 1px solid;
  color: #ffffff;
  border-radius: 10px;
}
.error {
  background: #c01332;
  border: #c01332 1px solid;
}
.success {
  background: #0c8d87;
  border: #0c8d87 1px solid;
}
.loading {
  background-image: linear-gradient(
    to right,
    #21223e 33%,
    #3c3f73 33% 66%,
    #21223e 66% 100%
  );
  background-size: 300% 300%;
  animation: loadingAnimation 5s linear infinite;
}
@keyframes loadingAnimation {
  0% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>
