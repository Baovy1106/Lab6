<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div id="app">
    <!-- Thanh menu bài tập -->
    <ul class="menu">
  <li class="list-group-item">Bài 1</li>
  <li class="list-group-item">Bài 2</li>
  <li class="list-group-item">Bài 3</li>
  <li class="list-group-item">Bài 4</li>
</ul>

    <!-- Khung nhập điểm -->
    <div class="wrapper">
      <h1>Nhập điểm trung bình:</h1>
      <input
        type="number"
        v-model="score"
        placeholder="Nhập điểm (0-10)"
        @input="DiemTB"
      />
      <p v-if="diemTB !== ''" class="output">Xếp loại: {{ diemTB }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      score: null, // Giá trị điểm trung bình nhập vào
      diemTB: "", // Lưu kết quả xếp loại
    };
  },
  methods: {
    DiemTB() {
      const score = parseFloat(this.score);
      if (isNaN(score) || score < 0 || score > 10) {
        this.diemTB = "Điểm không hợp lệ!";
      } else if (score < 5.0) {
        this.diemTB = "Yếu";
      } else if (score < 6.5) {
        this.diemTB = "Trung Bình";
      } else if (score < 8.0) {
        this.diemTB = "Khá";
      } else if (score < 9.0) {
        this.diemTB = "Giỏi";
      } else {
        this.diemTB = "Xuất Sắc";
      }
    },
  },
};
</script>

<style scoped>
/* Định dạng thanh menu */
.menu {
  display: flex;
  justify-content: space-between; /* Chia đều khoảng cách */
  padding: 15px;
  background-color: #f1f1f1;
  margin-bottom: 20px;
}

.menu-item {
  padding: 10px 20px;
  color: white;
  background-color: #007bff;
  text-decoration: none;
  font-size: 16px;
  font-weight: bold;
  border-radius: 5px;
  transition: background-color 0.3s, color 0.3s;
  text-align: center;
}

.menu-item:hover {
  background-color: #0056b3;
}

/* Định dạng tổng thể cho phần khung nhập */
.wrapper {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 0 auto;
  padding: 15px;
  max-width: 300px;
  background: #ffffff;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Tiêu đề */
h1 {
  color: #333;
  font-size: 20px;
  margin-bottom: 15px;
}

/* Ô nhập liệu */
input[type="number"] {
  width: 90%;
  padding: 8px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
  outline: none;
  transition: border-color 0.2s;
}

input[type="number"]:focus {
  border-color: #007bff;
}

/* Kết quả */
.output {
  font-size: 16px;
  color: #007bff;
  margin-top: 10px;
}
</style>
