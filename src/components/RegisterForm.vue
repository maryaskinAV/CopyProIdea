<template>
  <div class="register_form">
    <div class="inputs">
      <div class="inputWrp" v-for="(item, index) in arrOfInputs" :key="index">
        <div class="pWrp">
          <p>{{ item.text }}</p>
        </div>
        <input
          :type="item.input.type"
          :placeholder="
            placeholderChanger(item.input.placeholder, item.text, 1024)
          "
        />
      </div>
    </div>
    <div class="captcha">
      <div class="pWrp">
        <p>Capcha</p>
      </div>
      <div class="captchaWrp">
        <img src="@/assets/img/Register/captchatest.png" alt="" />
        <button>
          <img src="@/assets/img/Register/btnNewCaptcha.png" alt="" />
        </button>
      </div>
      <input type="text" placeholder="enter capcha" />
    </div>
    <div class="btnWrapper">
      <div class="agree">
        <input type="checkbox" />
        <p>I agree with terms</p>
      </div>
      <button>
        <p>Register</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegisterForm",
  props: ["arrOfInputs"],
  data() {
    return {
      widthProp: window.innerWidth,
    };
  },
  methods: {
    placeholderChanger: function (pcPlaceholder, mobilePlaceholder, number) {
      if (this.widthProp >= number) {
        return pcPlaceholder;
      } else {
        return mobilePlaceholder;
      }
    },
  },
  created() {
    window.addEventListener("resize", () => {
      this.widthProp = window.innerWidth;
    });
  },
};
</script>

<style lang="scss" scoped>
.register_form {
  & input:focus {
    border: 3px solid #a855f7;
  }
  @apply flex items-center flex-col mt-10 mb-10;
  & .inputs {
    @apply mb-0;
    @apply md:mb-3;
    & .inputWrp {
      @apply flex justify-between mb-4;
      @apply lg:-ml-28;
      & .pWrp {
        @apply hidden items-center justify-end w-28 mr-7;
        @apply lg:flex;
        & p {
          @apply justify-center text-blue-900;
        }
      }
      & input {
        @apply rounded-full text-left pl-8 h-14 w-72 transition-all duration-300 outline-none;
        @apply smlger:w-100 smlger:-ml-3;
        @apply lg:w-104 lg:m-0;
        background-color: rgba(243, 243, 243, 1);
      }
    }
  }
  & .captcha {
    @apply flex items-center w-56 justify-between flex-col;
    @apply lg:w-28.7rem lg:flex-row;
    & .pWrp {
      @apply -ml-13 mr-2.5;
      & p {
        @apply text-blue-900 hidden;
        @apply lg:block;
      }
    }
    .captchaWrp {
      @apply flex mb-3 w-60 justify-between;
      @apply lg:ml-0 lg:w-full lg:justify-center;
      & img {
        @apply w-44;
        @apply lg:w-38;
      }
      & button {
        @apply ml-5;
        & img {
          @apply w-7;
        }
      }
    }
    & input {
      @apply rounded-full text-left pl-10 h-14 w-52 mt-2 -mb-2 transition-all duration-300 outline-none;
      @apply lg:mt-0 lg:mb-2.5;
      background-color: rgba(243, 243, 243, 1);
    }
  }

  & .btnWrapper {
    @apply flex items-center w-56 flex-col justify-between mt-10;
    @apply lg:w-28.7rem lg:flex-row;
    & .agree {
      @apply flex items-center mb-2;
      @apply lg:ml-8 lg:mb-0;
      & input {
        @apply opacity-0 -mr-5 z-30;

        & + p::before {
          @apply inline-block w-4 h-4 rounded-full mr-2 transition-all duration-500;
          content: " ";
          border: 2px solid rgba(139, 92, 246, var(--tw-border-opacity));
        }

        &:checked + p::before {
          @apply bg-purple-500;
        }

        &:checked:hover + p::before {
          @apply bg-purple-500;
        }

        &:hover + p::before {
          @apply xl:bg-purple-300;
        }
      }

      & p {
        @apply text-gray-500 ml-1.5 flex items-center;
      }
    }
    & button {
      @apply text-gray-50 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full h-14 tracking-wide w-64 text-xl;
      @apply smplus:w-72 smplus:h-16;
      @apply lg:h-13 lg:w-60 lg:text-base;

      & p {
        @apply flex items-center flex-col;
        &::after {
          content: " ";
          @apply flex w-0 h-0 bg-blue-200 transition-all duration-700;
          border: 0px rgba(191, 219, 254, var(--tw-bg-opacity)) solid;
        }
      }
      &:hover {
        p {
          @apply -mb-0.5;
          &::after {
            content: " ";
            @apply flex w-1/4;
            border: 0.5px rgba(191, 219, 254, var(--tw-bg-opacity)) solid;
          }
        }
      }
    }
  }
}
</style>
