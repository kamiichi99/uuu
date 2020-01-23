<template>
  <div class="container">
    <div class="てすと">
      <form action="/charge" method="post" id="payment-form">
        <div class="form-row">
          <label for="card-element">
            クレジット・デビットカード番号
          </label>
          <div id="card-element">
            <!-- Stripe Element がここaaaに入ります。 -->
          </div>

          <!-- Element のエラーを入れます。 -->
          <div id="card-errors" role="alert"></div>
        </div>

        <button>お支払い</button>
      </form>
    </div>
    <div>
      <logo />
      <h1 class="title">
        uuu
      </h1>
      <h2 class="subtitle">
        My supreme Nuxt.js project
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
        <n-link to="test/test1">test</n-link>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  head() {
    return {
      script: [
        {
          src: "https://js.stripe.com/v3/"
        }
      ],
      link: [
        {
          rel: "stylesheet",
          href: "StripeElements.css"
        }
      ]
    };
  },
  components: {
    Logo
  },
  mounted() {
    var stripe = Stripe("pk_test_u9PIzGIDd8ka5ulZPXtVw5WH00dLoqhjdQ");
    var elements = stripe.elements();

    // Element作成時に options から スタイルを調整できます.
    var style = {
      base: {
        // ここでStyleの調整をします。
        fontSize: "16px",
        color: "#32325d"
      }
    };

    // card Element のインスタンスを作成
    var card = elements.create("card", { style: style });

    // マウント
    card.mount("#card-element");
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
