<template>
  <div>
    <DialogWindow :dialogConfig="dialog1Config" @submit="handleDialog1Submit" @cancel="handleCancel" />
    <DialogWindow :dialogConfig="dialog2Config" @submit="handleDialog2Submit" @cancel="handleCancel" />
  </div>
</template>

<script>
import DialogWindow from "@/components/DialogWindow.vue";

export default {
  components: {
    DialogWindow,
  },
  data() {
    return {
      dialog1Config: {
        fields: [
          { name: "manager", label: "Менеджер", type: "Dropdown", options: ["Менеджер1", "Менеджер2"] },
          { name: "productName", label: "Название продукта", type: "Input", placeholder: "Введите название" },
          { name: "jiraLink", label: "Ссылка в Jira", type: "Input", placeholder: "Введите ссылку" },
          { name: "domain", label: "Домен", type: "Dropdown", options: ["Бэк-офис", "Техплатформа"] },
        ],
      },
      dialog2Config: {
        fields: [
          { name: "employee", label: "Сотрудник", type: "Dropdown", options: ["Сотрудник1", "Сотрудник2"] },
          { name: "manager", label: "Руководитель сотрудника", type: "Dropdown", options: ["Руководитель1", "Руководитель2"] },
          { name: "rateType", label: "Тип ставки", type: "Dropdown", options: ["opex", "capex"] },
          { name: "businessUnit", label: "Бизнес-единица", type: "Dropdown", options: ["MVM", "MTech"] },
          { name: "capitalizationPercentage", label: "Процент капитализации", type: "Input", placeholder: "Введите процент" },
          { name: "position", label: "Должность", type: "Input", placeholder: "Введите должность" },
        ],
      },
    };
  },
  methods: {
    handleDialog1Submit(data) {
      // Обработка отправки данных для диалога 
      console.log("Данные диалога 1:", data);
    },
    handleDialog2Submit(data) {
      console.log("Данные диалога 2:", data);
    },
    handleCancel() {
      // Обработка отмены
      console.log("Диалог отменен");
    },
  },
};
</script>