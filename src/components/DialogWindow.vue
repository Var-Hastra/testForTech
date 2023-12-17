<template>
  <div class="dialog-window">
    <!-- Отображение полей диалога -->
    <div v-for="field in dialogConfig.fields" :key="field.name" class="form-field">
      <label :for="field.name">{{ field.label }}:</label>
      <!-- Проверка типа поля -->
      <template v-if="field.type === 'Dropdown'">
        <select v-model="formData[field.name]" class="dropdown">
          <option v-for="option in field.options" :key="option">{{ option }}</option>
        </select>
      </template>
      <template v-else-if="field.type === 'Input'">
        <input
          v-model="formData[field.name]"
          :type="field.inputType || 'text'"
          :placeholder="field.placeholder"
          class="input"
        />
      </template>
    </div>
    <button @click="handleSubmit" class="submit-btn">Отправить</button>
    <button @click="handleCancel" class="cancel-btn">Отмена</button>
  </div>
</template>

<script>
export default {
  props: {
    dialogConfig: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      formData: {}, // Хранение данных формы
    };
  },
  methods: {
    handleSubmit() {
      // Вызывается при отправке формы
      this.$emit("submit", this.formData);
      this.resetForm();
    },
    handleCancel() {
      // Вызывается при отмене формы
      this.$emit("cancel");
      this.resetForm();
    },
    resetForm() {
      this.formData = {};
    },
  },
};
</script>

<style scoped>
/* Стили компонента */
.dialog-window {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.form-field {
  margin-bottom: 10px;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

.dropdown,
.input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 5px;
}

.submit-btn,
.cancel-btn {
  background-color: #007bff;
  color: #fff;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-right: 10px;
}

.submit-btn:hover,
.cancel-btn:hover {
  background-color: #0056b3;
}


</style>
