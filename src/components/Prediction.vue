<template>
  <section class="prediction">
    <div class="container">
      <div class="prediction__head">
        <div>
          <label class="prediction__label" for="term"
            >Выберите подходящий масштаб:</label
          >
          <select id="term" class="prediction__select" v-model="term">
            <option value="1">Между ценами сутки</option>
            <option value="2">Между ценами неделя</option>
            <option value="3">Между ценами месяц</option>
            <option value="4">Между ценами год</option>
          </select>
        </div>
        <div>
          <label class="prediction__label" for="count"
            >Введите количество {{ terms }}:</label
          >
          <input
            id="count"
            class="prediction__input"
            type="number"
            v-model="count"
            min="1"
            max="20"
          />
        </div>
      </div>
      <form class="prediction__body" v-on:submit="predict">
        <div v-for="index in count" :key="index">
          <label class="prediction__label" :for="'price-' + index"
            >Цена {{ count + 1 - index }} {{ terms }} назад:</label
          >
          <input
            :id="'price-' + index"
            class="prediction__input"
            type="number"
            v-model="prices[index - 1]"
            min="0"
            step="0.01"
            required
          />
        </div>
        <button class="prediction__submit" type="submit">
          Предположить будущую стоимость
        </button>
      </form>
      <div class="prediction__output" v-if="price && advice">
        <div class="prediction__row">
          <span>Предполагаемая цена</span>
          <span class="prediction__alarm">{{ price }}</span>
        </div>
        <div class="prediction__row">
          <span>Наш совет</span>
          <span class="prediction__alarm">{{ advice }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import * as tf from "@tensorflow/tfjs";

export default {
  name: "Prediction",
  data() {
    return {
      term: "1",
      count: 4,
      prices: [],
      X_max: 1,
      X_min: 0,
      price: null,
      advice: null,
    };
  },
  computed: {
    terms() {
      if (this.term === "1") return "дней";
      else if (this.term === "2") return "недель";
      else if (this.term === "3") return "месяцев";
      else if (this.term === "4") return "лет";

      return "чего-то";
    },
  },
  methods: {
    fit(X, min = 0, max = 1) {
      this.X_max = Math.max.apply(null, X);
      this.X_min = Math.min.apply(null, X);
      // console.log(this.X_max + " " + this.X_min)
      let min_ = min;
      let max_ = max;

      var X_minArr = X.map((values) => {
        return values - this.X_min;
      });
      // X_std = (X - X.min()) / (X.max() - X.min())
      var X_std = X_minArr.map((values) => {
        return values / (this.X_max - this.X_min);
      });
      // X_scaled = X_std * (max - min) + min
      return X_std.map(function (values) {
        return values * (max - min) + min;
      });
    },
    inverse_transform(input, min = 0, max = 1) {
      // var fit = get_params();

      var X = input.map(function (values) {
        return (values - min) / (max - min);
      });
      var X_ = X.map((values) => {
        return values * (this.X_max - this.X_min) + this.X_min;
      });

      return X_;
    },
    predict(event) {
      event.preventDefault();

      // второй вариант почему-то лучше (?)
      // let array = this.fit(this.prices);
      let array = this.prices;
      let arrayForPredict = tf.reshape(array, [array.length, 1, 1]);

      tf.loadLayersModel("/model/model.json").then(model => {
        model
          .predict(arrayForPredict)
          .array()
          .then((res) => {
            res = this.inverse_transform(res);
            this.price = res[res.length - 1];

            let tenPercents = this.prices[this.prices.length - 1] / 10;
            if (this.prices[res[res.length - 1] - this.prices.length - 1] > tenPercents) {
              this.advice = 'покупать с избытком';
            } else if(this.prices[this.prices.length - 1] - res[res.length - 1] > tenPercents) {
              this.advice = 'срочно продавать';
            } else {
              this.advice = 'продолжать держать в портфеле';
            }
          });
      });
    }
  }
};
</script>

<style lang="scss">
.prediction {
  padding: 60px 0;

  .prediction__head {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }

  .prediction__body {
    margin-top: 30px;
    padding-top: 30px;
    border-top: 1px solid #9ca3af;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }

  .prediction__label {
    display: block;
    margin-bottom: 4px;
    font-size: 12px;
  }

  .prediction__select,
  .prediction__input {
    display: block;
    width: 100%;
    outline: none;
    padding: 6px 10px;
    border: 1px solid #9ca3af;
    border-radius: 6px;
    background-color: transparent;
    font-weight: inherit;
    color: inherit;
    transition: 0.3s;

    &:focus {
      border: 1px solid #4b5563;
    }
  }

  .prediction__submit {
    grid-column: 1 / 3;
    outline: none;
    padding: 10px;
    cursor: pointer;
    background-color: #6b7280;
    text-transform: uppercase;
    font-family: inherit;
    font-size: 12px;
    border: 1px solid transparent;
    border-radius: 6px;
    font-weight: 500;
    color: #fff;
    transition: 0.3s;

    &:hover {
      background-color: #4b5563;
    }
  }

  .prediction__output {
    margin-top: 60px;
    background-color: #fff;
    border-radius: 6px;
    border: 1px solid #6b7280;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .prediction__row {
    display: flex;
    justify-content: space-between;
  }

  .prediction__alarm {
    font-weight: 500;
  }

  @media (max-width: 768px) {
    .prediction__head {
      grid-template-columns: 1fr;
    }

    .prediction__body {
      grid-template-columns: 1fr;
    }

    .prediction__submit {
      grid-column: 1 / 2;
    }
  }
}
</style>
