<template>
  <div class="custom-dropdown">
    <button class="dropdown-toggle" @click="toggleDropdown">
      Open Dropdown
    </button>
    <div class="dropdown-list" :class="{ active: dropdownOpen }">
      <label
        v-for="option in options"
        :key="option.value"
        class="dropdown-option"
      >
        <input
          type="checkbox"
          :value="option.value"
          v-model="selectedOptions"
        />
        {{ option.label }}
      </label>
    </div>
  </div>
  <div class="selected-options">
    <div
      v-for="selected in selectedOptions"
      :key="selected"
      class="selected-option"
    >
      {{ selected }}
      <button @click="removeSelected(selected)">X</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const options = [
  { value: "Áustria", label: "Áustria" },
  { value: "Austrália", label: "Austrália" },
  { value: "Bélgica", label: "Bélgica" },
  { value: "Brasil", label: "Brasil" },
  { value: "Canadá", label: "Canadá" },
  { value: "China", label: "China" },
];

const selectedOptions = ref([]);
const dropdownOpen = ref(false);

const toggleDropdown = () => {
  dropdownOpen.value = !dropdownOpen.value;
};

const removeSelected = (item) => {
  selectedOptions.value = selectedOptions.value.filter(
    (option) => option !== item
  );
};
</script>

<style scoped>
.custom-dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-toggle {
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  padding: 5px 10px;
  cursor: pointer;
}

.dropdown-list {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: white;
  border: 1px solid #ccc;
  padding: 10px;
  display: none;
}

.dropdown-option {
  display: block;
  margin-bottom: 5px;
}

.dropdown-list.active {
  display: block;
}

.selected-options {
  margin-top: 10px;
}

.selected-option {
  background-color: #f0f0f0;
  border-radius: 5px;
  padding: 5px 10px;
  display: inline-flex;
  align-items: center;
  margin-right: 5px;
}

.selected-option button {
  margin-left: 10px;
  background-color: gray;
  border: none;
  color: white;
  border-radius: 50%;
  cursor: pointer;
  width: 20px;
  height: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
