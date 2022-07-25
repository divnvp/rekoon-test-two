<script setup>
import { defineProps, defineEmits } from "vue";

defineProps({
  modelValue: { type: Boolean, required: true }
});

defineEmits(["update:modelValue", "close"]);

const mailParams = [
  "Сеть",
  "Регион",
  "Город",
  "Округ",
  "Район",
];

const addresses = [
  { id: 1, number: "1", index: "ПО_105064", city: "Москва", street: "ул. Земляной Вал, 2", reach: 10432 },
  { id: 2, number: "1", index: "ПО_105064", city: "Москва", street: "ул. Земляной Вал, 2", reach: 10432 },
  { id: 3, number: "1", index: "ПО_105064", city: "Москва", street: "ул. Земляной Вал, 2", reach: 10432 },
  { id: 4, number: "1", index: "ПО_105064", city: "Москва", street: "ул. Земляной Вал, 2", reach: 10432 },
  { id: 5, number: "1", index: "ПО_105064", city: "Москва", street: "ул. Земляной Вал, 2", reach: 10432 },
]
</script>

<template>
  <section v-if="modelValue" class="modal-container">
    <div class="modal__body">
      <header class="modal__body_header">
        <span class="modal__title">Почтовые отделения</span>

        <button @click="$emit('close')" class="modal__button_close">
          <img src="../assets/close.png" />
        </button>
      </header>

      <main class="modal__main">
        <aside class="modal__main__search">
          <span class="modal__main__description">
            Воспользуйтесь поиском и фильтром, чтобы подобрать
            почтовые отделения
          </span>

          <button class="modal__main__button_search">
            Найти на карте
          </button>
        </aside>
        
        <aside class="modal__main__mail">
          <span class="modal__main__mail_title">Почтовые отделения</span>

          <div class="modal__main__mail-params">
            <section
              v-for="param in mailParams"
              :key="param"
              class="modal__main__mail-params_box"
            >
              <span class="modal__main__mail-params_box__name">
                {{ param }}
              </span>
            </section>
          </div>
          
        </aside>

        <aside class="modal__main__filter">
          <div class="modal__main__filter_group">
            <div class="modal__main__filter_seacrh">
              <input
                placeholder="Введите адрес или индекс"
                class="modal__main__filter_seacrh__input"
              >

              <img src="../assets/search.png" />
            </div>
            
            <select class="modal__main__filter_select">
              <optgroup>
                <option selected>ФИЛЬТР</option>
                <option>ФИЛЬТР</option>
                <option>ФИЛЬТР</option>
                <option>ФИЛЬТР</option>
                <option>ФИЛЬТР</option>
              </optgroup>
            </select>
          </div>
          
          <div class="modal__main__filter_group">
            <button class="modal__button_gray delete">
              Удалить
            </button>

            <button class="modal__button_gray clear">
              Очистить
            </button>
          </div>
        </aside>

        <aside class="row">
          <section class="col">
            <div>
              <div class="table">
                <span class="table__header table__header__number__margin">№</span>
                <span class="table__header table__header__index__margin">ИНДЕКС</span>
                <span class="table__header table__header__city__margin">ГОРОД</span>
                <span class="table__header table__header__street__margin">АДРЕС</span>

                <select class="table__header table__header__select">
                  <option>REACH</option>
                  <option>REACH</option>
                  <option>REACH</option>
                  <option>REACH</option>
                </select>
              </div>
              
              <div class="table__body">
                <div
                  v-for="address in addresses"
                  :key="address.id"
                  class="table__body_row"
                >
                  <button>
                    +
                  </button>
                  <span>{{ address.number }}</span>
                  <hr />

                  <span style="width: 80px">{{ address.index }}</span>
                  <hr />

                  <span>{{ address.city }}</span>
                  <img src="../assets/map-pin.png" />
                  <hr />

                  <span>{{ address.street }}</span>
                  <hr />

                  <span>{{ address.reach }}</span>
                </div>
              </div>
            </div>
          </section>

          <section class="col">
            <div class="po-box">
              <div class="po">
                <span
                  v-for="n in 5" :key="n"
                >
                  ПО_105064
                </span>
              </div>

              <button class="modal__button_calc">
                РАССЧИТАТЬ
              </button>
            </div>
          </section>
        </aside>
      </main>

      <footer class="footer">
        
      </footer>
    </div>
  </section>
</template>

<style lang="scss">
.modal {
  &-container {
    display: flex;
    justify-content: center;
    align-items: center;
    
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: rgba(4, 8, 17, 0.5);
  }
}

.col {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
}

@media screen and (min-width: 1008px){
.modal {
  &__title {
    font-weight: 600;
    font-size: 20px;
    line-height: 30px;
    color: #040811;
  }

  &__body {
    margin: 120px 235px;
    background-color: white;
    border-radius: 3px;
    padding: 32px 40px;
    max-width: calc(970px - 40px);

    display: flex;
    flex-direction: column;

    &_header {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;
    }
  }

   &__button_close {
    display: flex;
    flex-direction: row;
    align-items: center;

    border: none;
    background-color: transparent;
  }

  &__button_gray {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin-left: 16px;

    background: #EEF2FB;
    border-radius: 3px;

    border: none;
    padding: 12px 24px;

    font-weight: 700;
    font-size: 12px;
    line-height: 16px;
    /* identical to box height, or 133% */

    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #040811;

    .delete {
      width: 118px;
    }

    .clear {
      width: 124px;
    }
  }

  &__button_calc {
    background: #E90D00;
    box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
    border-radius: 3px;

    border: none;

    padding: 14px;

    font-weight: 700;
    font-size: 14px;
    line-height: 20px;

    text-align: center;
    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #FFFFFF;

    width: 242px;

    margin-top: 16px;
  }

  &__main {
    display: flex;
    flex-direction: column;
    flex: 1 1 0;

    margin-top: 8px;

    &__search {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      flex: 1 1 0;
    }

    &__description {
      display: flex;

      font-weight: 400;
      font-size: 14px;
      line-height: 20px;
      color: #4F5258;

      width: 407px;
    }

    &__button_search {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      width: 171px;
      height: 40px;

      background: #E90D00;
      box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
      border-radius: 3px;

      font-weight: 700;
      font-size: 12px;
      line-height: 16px;

      letter-spacing: 0.05em;
      text-transform: uppercase;

      color: #FFFFFF;

      border: none;
    }

    &__mail {
      display: flex;
      flex-direction: column;

      border: 1px solid #D9DADB;
      border-radius: 3px;

      margin-top: 39px;

      &_title {
        position: absolute;
        margin-top: -10px;
        margin-left: -1px;

        background: white;
        width: 230px;
        height: 50px;

        font-weight: 600;
        font-size: 14px;
        line-height: 22px;

        text-transform: uppercase;

        color: #040811;
      }

      &-params {
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        padding: 15px;
        margin-top: 24px;

        z-index: 99;

        &_box {
          display: flex;

          width: 160px;
          height: 200px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          &__name {
            padding: 16px;
          }
        }
      }
    }

    &__filter {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;

      margin-top: 24px;

      &_group {
        display: flex;
      }

      &_seacrh {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-end;

        input {
          width: 451px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          padding: 10px 16px;

          &::placeholder {
            font-weight: 400;
            font-size: 14px;
            line-height: 20px;

            color: #9B9CA0;
          }
        }

        img {
          position: absolute;
          margin-right: 12px;
        }
      }

      &_select {
        margin-left: 16px;

        border: 1px solid #D9DADB;
        border-radius: 3px;

        font-weight: 600;
        font-size: 12px;
        line-height: 16px;
        color: #4F5258;

        padding: 12px 16px;

        margin-right: 18px;
      }
    }
  }
}

.table {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;

  margin-top: 16px;

  background: #EEF2FB;
  border-radius: 3px;

  padding: 14px 56px;

  max-width: calc(586px - 76px);
  max-height: 100px;

  &__header {
    font-weight: 600;
    font-size: 12px;
    line-height: 20px;

    text-transform: uppercase;

    color: #4F5258;

    &__select {
      border: none;
      background-color: transparent;
    }

    &__number__margin {
      margin-right: 50px;
    }

    &__index__margin {
      margin-right: 72px;
    }
    
    &__city__margin {
      margin-right: 90px
    }

    &__street__margin {
      margin-right: 85px
    }
  }

  &__body {
    display: flex;
    flex-direction: row;
    flex: 1 1 0;

    margin-top: calc(20px - 12px);
    max-height: 350px;
    
    display: inline-block;
    overflow-y: auto;
    white-space: nowrap;

    ::-webkit-scrollbar{
        height: 4px;
        width: 4px;
        background: gray;
    }

    ::-webkit-scrollbar-thumb:horizontal{
        background-color: #000;
        border-radius: 10px;
    }

    &_row {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: center;

      padding: 24px 32px;

      border-bottom: 1px solid #D9DADB;

      hr {
        width: 32px;
        height: 0px;

        border: 1px solid #D9DADB;
        transform: rotate(90deg);
      }

      button {
        border-radius: 50%;

        border: 1px solid #2D00FF;
        background: white;
        margin-right: 18px;
      }

      img {
        margin-left: 8px;
      }
    }
  }
}

.po {
  display: flex;
  flex-direction: column;
  gap: 14px;

  border: 1px solid #D9DADB;
  border-radius: 3px;

  width: calc(256px - 24px * 2 - 15px);
  height: 321px;

  margin-top: 16px;

  padding: 24px;

  font-weight: 500;
  font-size: 16px;
  line-height: 22px;

  color: #4F5258;

  &-box {
    display: flex;
    flex-direction: column;
    margin-left: 65px;
  }
}
}

@media screen and (min-width: 641px) and (max-width: 1007px) {
.modal {
  &__title {
    font-weight: 600;
    font-size: 12px;
    line-height: 30px;
    color: #040811;
  }

  &__body {
    margin: 120px 235px;
    background-color: white;
    border-radius: 3px;
    padding: 32px 40px;
    max-width: calc(570px - 40px);

    display: flex;
    flex-direction: column;

    &_header {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;
    }
  }

   &__button_close {
    display: flex;
    flex-direction: row;
    align-items: center;

    border: none;
    background-color: transparent;
  }

  &__button_gray {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin-left: 16px;

    background: #EEF2FB;
    border-radius: 3px;

    border: none;
    padding: 8px 12px;

    font-weight: 700;
    font-size: 8px;
    line-height: 16px;
    /* identical to box height, or 133% */

    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #040811;

    .delete {
      width: 118px;
    }

    .clear {
      width: 124px;
    }
  }

  &__button_calc {
    background: #E90D00;
    box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
    border-radius: 3px;

    border: none;

    padding: 7px;

    font-weight: 700;
    font-size: 10px;
    line-height: 20px;

    text-align: center;
    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #FFFFFF;

    width: 150px;

    margin-top: 8px;
  }

  &__main {
    display: flex;
    flex-direction: column;
    flex: 1 1 0;

    margin-top: 8px;

    &__search {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      flex: 1 1 0;
    }

    &__description {
      display: flex;

      font-weight: 400;
      font-size: 12px;
      line-height: 20px;
      color: #4F5258;

      width: 407px;
    }

    &__button_search {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      width: 141px;
      height: 30px;

      background: #E90D00;
      box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
      border-radius: 3px;

      font-weight: 700;
      font-size: 8px;
      line-height: 16px;

      letter-spacing: 0.05em;
      text-transform: uppercase;

      color: #FFFFFF;

      border: none;
    }

    &__mail {
      display: flex;
      flex-direction: column;

      border: 1px solid #D9DADB;
      border-radius: 3px;

      margin-top: 19px;

      &_title {
        position: absolute;
        margin-top: -10px;
        margin-left: -1px;

        background: white;
        width: 150px;
        height: 40px;

        font-weight: 600;
        font-size: 10px;
        line-height: 22px;

        text-transform: uppercase;

        color: #040811;
      }

      &-params {
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        padding: 10px;
        margin-top: 8px;

        z-index: 99;

        &_box {
          display: flex;

          width: 80px;
          height: 100px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          &__name {
            padding: 16px;

            font-size: 12px;
          }
        }
      }
    }

    &__filter {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;

      margin-top: 7px;

      &_group {
        display: flex;
      }

      &_seacrh {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-end;

        input {
          width: 191px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          padding: 5px 8px;

          &::placeholder {
            font-weight: 400;
            font-size: 14px;
            line-height: 20px;

            color: #9B9CA0;
          }
        }

        img {
          position: absolute;
          margin-right: 6px;
        }
      }

      &_select {
        margin-left: 16px;

        border: 1px solid #D9DADB;
        border-radius: 3px;

        font-weight: 600;
        font-size: 10px;
        line-height: 16px;
        color: #4F5258;

        padding: 5px 8px;

        margin-right: 8px;
      }
    }
  }
}

.table {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;

  margin-top: 8px;

  background: #EEF2FB;
  border-radius: 3px;

  padding: 7px 10px;

  max-width: calc(320px - 10px);
  max-height: 100px;

  &__header {
    font-weight: 600;
    font-size: 8px;
    line-height: 20px;

    text-transform: uppercase;

    color: #4F5258;

    &__number__margin {
      margin-right: 15px;
    }

    &__index__margin {
      margin-right: 32px;
    }
    
    &__city__margin {
      margin-right: 50px
    }

    &__street__margin {
      margin-right: 45px
    }

    &__select {
      border: none;
      background-color: transparent;
    }
  }

  &__body {
    display: flex;
    flex-direction: row;
    flex: 1 1 0;

    margin-top: 8px;
    max-height: 250px;
    
    display: inline-block;
    overflow-y: auto;
    white-space: nowrap;

    font-size: 8px;

    ::-webkit-scrollbar{
        height: 4px;
        width: 4px;
        background: gray;
    }

    ::-webkit-scrollbar-thumb:horizontal{
        background-color: #000;
        border-radius: 10px;
    }

    &_row {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: center;

      padding: 4px 2px;

      border-bottom: 1px solid #D9DADB;

      hr {
        width: 12px;
        height: 0px;

        border: 1px solid #D9DADB;
        transform: rotate(90deg);
      }

      button {
        border-radius: 50%;

        border: 0.5px solid #2D00FF;
        background: white;
        margin-right: 8px;

        font-size: 8px;
        width: 10px;

        display: flex;
        align-items: center;
        justify-content: center;
      }

      img {
        margin-left: 8px;
      }
    }
  }
}

.po {
  display: flex;
  flex-direction: column;
  gap: 4px;

  border: 1px solid #D9DADB;
  border-radius: 3px;

  width: 120px;
  height: 121px;

  margin-top: 16px;

  padding: 14px;

  font-weight: 500;
  font-size: 8px;
  line-height: 22px;

  color: #4F5258;

  &-box {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    
    margin-left: -130px;
  }
}

.index__margin {
  margin-right: 72px;
}

.city__margin {
  margin-right: 90px
}

.street__margin {
  margin-right: 85px
}
}

@media screen and (max-width: 640px) {
.modal {
  &__title {
    font-weight: 600;
    font-size: 9px;
    line-height: 30px;
    color: #040811;
  }

  &__body {
    margin: 20px 35px;
    background-color: white;
    border-radius: 3px;
    padding: 12px 10px;
    max-width: 300px;

    display: flex;
    flex-direction: column;

    &_header {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;
    }
  }

   &__button_close {
    display: flex;
    flex-direction: row;
    align-items: center;

    border: none;
    background-color: transparent;
  }

  &__button_gray {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin-left: 6px;

    background: #EEF2FB;
    border-radius: 3px;

    border: none;
    padding: 5px 6px;

    font-weight: 700;
    font-size: 6px;
    line-height: 16px;

    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #040811;

    .delete {
      width: 18px;
    }

    .clear {
      width: 24px;
    }
  }

  &__button_calc {
    background: #E90D00;
    box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
    border-radius: 3px;

    border: none;

    padding: 7px;

    font-weight: 700;
    font-size: 7px;
    line-height: 10px;

    text-align: center;
    letter-spacing: 0.05em;
    text-transform: uppercase;

    color: #FFFFFF;

    width: 95px;

    margin-top: 4px;
  }

  &__main {
    display: flex;
    flex-direction: column;
    flex: 1 1 0;

    margin-top: 1px;

    &__search {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      flex: 1 1 0;
    }

    &__description {
      display: flex;

      font-weight: 400;
      font-size: 8px;
      line-height: 10px;
      color: #4F5258;

      width: 207px;
    }

    &__button_search {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      width: 100px;
      height: 20px;

      background: #E90D00;
      box-shadow: 0px 0px 15px rgba(233, 13, 0, 0.25);
      border-radius: 3px;

      font-weight: 700;
      font-size: 8px;
      line-height: 16px;

      letter-spacing: 0.05em;
      text-transform: uppercase;

      color: #FFFFFF;

      border: none;
    }

    &__mail {
      display: flex;
      flex-direction: column;

      border: 1px solid #D9DADB;
      border-radius: 3px;

      margin-top: 9px;

      &_title {
        position: absolute;
        margin-top: -10px;
        margin-left: -1px;

        background: white;
        width: 150px;
        height: 20px;

        font-weight: 600;
        font-size: 8px;
        line-height: 22px;

        text-transform: uppercase;

        color: #040811;
      }

      &-params {
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        padding: 5px;
        margin-top: 8px;

        z-index: 99;

        &_box {
          display: flex;

          width: 50px;
          height: 50px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          &__name {
            padding: 6px;

            font-size: 8px;
          }
        }
      }
    }

    &__filter {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      flex: 1 1 0;

      margin-top: 7px;

      &_group {
        display: flex;
      }

      &_seacrh {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-end;

        input {
          width: 100px;

          border: 1px solid #D9DADB;
          border-radius: 3px;

          padding: 5px 8px;

          &::placeholder {
            font-weight: 400;
            font-size: 7px;
            line-height: 20px;

            color: #9B9CA0;
          }
        }

        img {
          position: absolute;
          margin-right: 6px;
          background: white;
        }
      }

      &_select {
        margin-left: 5px;

        border: 1px solid #D9DADB;
        border-radius: 3px;

        font-weight: 600;
        font-size: 6px;
        line-height: 6px;
        color: #4F5258;

        padding: 1px 2px;
      }
    }
  }
}

.table {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;

  margin-top: 4px;

  background: #EEF2FB;
  border-radius: 3px;

  padding: 1px 20px;

  max-width: 145px;
  max-height: 500px;

  &__header {
    font-weight: 600;
    font-size: 6px;
    line-height: 10px;

    text-transform: uppercase;

    color: #4F5258;

    &__number__margin {
      margin-right: 5px;
    }

    &__index__margin {
      margin-right: 19px;
    }
    
    &__city__margin {
      margin-right: 10px
    }

    &__street__margin {
      margin-right: 5px
    }

    &__select {
      border: none;
      background-color: transparent;
    }
  }

  &__body {
    display: flex;
    flex-direction: row;
    flex: 1 1 0;

    margin-top: 8px;
    max-height: 250px;
    width: 180px;
    
    display: inline-block;
    overflow-y: auto;
    white-space: nowrap;

    font-size: 6px;

    ::-webkit-scrollbar{
        height: 4px;
        width: 4px;
        background: gray;
    }

    ::-webkit-scrollbar-thumb:horizontal{
        background-color: #000;
        border-radius: 10px;
    }

    &_row {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: center;

      padding: 1px 1px;

      border-bottom: 1px solid #D9DADB;

      hr {
        width: 12px;
        height: 0px;

        border: 1px solid #D9DADB;
        transform: rotate(90deg);
      }

      button {
        border-radius: 50%;

        border: 0.5px solid #2D00FF;
        background: white;
        margin-right: 8px;

        font-size: 8px;
        width: 5px;

        display: flex;
        align-items: center;
        justify-content: center;
      }

      img {
        margin-left: 2px;
        width: 5px;
      }
    }
  }
}

.po {
  display: flex;
  flex-direction: column;
  gap: 4px;

  border: 1px solid #D9DADB;
  border-radius: 3px;

  width: 85px;
  height: 51px;

  margin-top: 6px;

  padding: 4px;

  font-weight: 500;
  font-size: 6px;
  line-height: 5px;

  color: #4F5258;

  &-box {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
}
}
</style>
