<template>
  <div class="container">
    <h1>Dompetku – Expense & Income Money Management</h1>
    <div class="form">
      <input
        type="text"
        v-model="newEntry.description"
        placeholder="Keterangan"
        class="input"
      />
      <input
        type="number"
        v-model.number="newEntry.amount"
        placeholder="Jumlah Uang"
        class="input"
      />
      <button @click="addEntry" class="btn">Submit</button>
    </div>

    <div class="list">
      <h2>Rekap Keuangan</h2>
      <div v-if="entries.length === 0">Belum ada data.</div>
      <ul>
        <li v-for="(entry, index) in entries" :key="index" class="entry-item">
          <span>{{ entry.description }} - Rp {{ entry.amount }}</span>
          <button @click="removeEntry(index)" class="delete-btn">Hapus</button>
        </li>
      </ul>
      <button @click="clearAllEntries" class="clear-btn">Hapus Semua Data</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newEntry: {
        description: "",
        amount: null,
      },
      entries: [],
    };
  },
  methods: {
    addEntry() {
      if (this.newEntry.description && this.newEntry.amount) {
        this.entries.push({
          description: this.newEntry.description,
          amount: this.newEntry.amount,
        });
        this.newEntry.description = "";
        this.newEntry.amount = null;
      } else {
        alert("Harap isi keterangan dan jumlah uang.");
      }
    },
    removeEntry(index) {
      this.entries.splice(index, 1);
    },
    clearAllEntries() {
      this.entries = [];
    },
  },
};
</script>

<style>
/* Background and container styles */
body {
  background: #f0f4f8;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  max-width: 450px;
  background: #ffffff;
  padding: 30px 20px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  text-align: center;
  color: #333;
  transition: box-shadow 0.3s ease;
}

.container:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

/* Form styles */
.form {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 20px;
}

.input {
  padding: 12px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  transition: border-color 0.3s ease;
}

.input:focus {
  border-color: #4caf50;
  outline: none;
}

.btn {
  padding: 12px;
  background-color: #4caf50;
  color: white;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #43a047;
}

/* List styles */
.list {
  margin-top: 25px;
}

.entry-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 15px;
  background: #f9fafb;
  border: 1px solid #e0e4e7;
  border-radius: 8px;
  margin-bottom: 10px;
  transition: background-color 0.2s ease;
}

.entry-item:hover {
  background-color: #e8f5e9;
}

.entry-item span {
  font-size: 16px;
  color: #444;
}

.delete-btn {
  background-color: #ef5350;
  border: none;
  color: white;
  font-size: 14px;
  padding: 6px 10px;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.delete-btn:hover {
  background-color: #e53935;
}

.clear-btn {
  margin-top: 25px;
  background-color: #ff7043;
  color: white;
  border: none;
  font-weight: bold;
  padding: 12px;
  width: 100%;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.clear-btn:hover {
  background-color: #f4511e;
}

/* Heading styles */
h1 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #4caf50;
}

h2 {
  font-size: 20px;
  color: #444;
  margin-top: 20px;
  margin-bottom: 15px;
}
</style>
