<template>
  <form>
    <div v-for="people in formData" :key="people.pk">
      <label>
        {{people.text}}
      </label>
      <div v-for="quest in people.quests" :key="quest.pk">
        <label>
          {{quest.text}}<br>
          <input type="range" min="0" max="5" :name="quest.name" value="0">
        </label>
      </div>
    </div>
    <input type="button" value="Отправить!" v-on:click="sendForm">
  </form>
</template>

<script>
  export default {
    name: "monthly",
    data: function () {
      return {
        kek: "kek",
        formData: [{'pk': 0, 'text': "", 'quests': []}],
      }
    },
    methods: {
      sendForm: function () {

      }
    },
    mounted() {
      this.$feeapi.monthly.getForm(r => {
        this.formData = r;
      });
    }
  }
</script>

<style scoped>

</style>
