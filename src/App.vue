<template>
  <div class="container">
    <h1 class="title">Font Style Generator</h1>
    <div class="form-container">
      <p>Masukkan Teks Dibawah Ini :</p>
      <input
        type="text"
        v-model="inputText"
        placeholder="Masukkan Teks Disini.."
        :class="{ highlight: inputText.includes('Vue') }"
        :style="{ 'font-weight': fontWeight, 'font-style': fontStyle, 'text-decoration': textDecoration, 'color': textColor, 'font-size': fontSize + 'px', 'font-family': fontFamily }"
        class="text-input"
        @input="handleInputChange"
      />
      <p>
        Output :
        <br />
        <span class="wrapped-text" :style="{ 'font-weight': fontWeight, 'font-style': fontStyle, 'text-decoration': textDecoration, 'color': textColor, 'font-size': fontSize + 'px', 'font-family': fontFamily }">{{ inputText }}</span>
      </p>
      
      <div class="option-group">
        <p>Gaya :</p>
        <div>
          <button @click="toggleBold">Bold</button>
          <button @click="toggleItalic">Italic</button>
          <button @click="toggleUnderline">Underline</button>
        </div>
      </div>
      <!-- Kelompokkan pilihan warna teks -->
      <div class="option-group">
        <p>Warna :</p>
        <div>
          <button @click="changeTextColor('black')">Hitam</button>
          <button @click="changeTextColor('red')">Merah</button>
          <button @click="changeTextColor('blue')">Biru</button>
          <button @click="changeTextColor('green')">Hijau</button>
          <button @click="changeTextColor('purple')">Ungu</button>
        </div>
      </div>
      <!-- Kelompokkan pilihan ukuran font -->
      <div class="option-group">
        <p>Ukuran Font:</p>
        <div>
          <button @click="changeFontSize(12)">Kecil</button>
          <button @click="changeFontSize(16)">Sedang</button>
          <button @click="changeFontSize(20)">Besar</button>
        </div>
      </div>
      <!-- Kelompokkan pilihan jenis font -->
      <div class="option-group">
        <p>Jenis Font:</p>
        <div>
          <button @click="changeFontFamily('Arial, sans-serif')">Arial</button>
          <button @click="changeFontFamily('Times New Roman, serif')">Times New Roman</button>
          <button @click="changeFontFamily('Courier New, monospace')">Courier New</button>
          <button @click="changeFontFamily('Verdana, sans-serif')">Verdana</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: "",
      fontWeight: "normal",
      fontStyle: "normal",
      textDecoration: "none",
      textColor: "black",
      fontSize: 16,
      fontFamily: "Arial, sans-serif"
    };
  },
  methods: {
    handleInputChange(event) {
      console.log("Nilai input berubah:", event.target.value);
    },
    toggleBold() {
      this.fontWeight = this.fontWeight === "bold" ? "normal" : "bold";
    },
    toggleItalic() {
      this.fontStyle = this.fontStyle === "italic" ? "normal" : "italic";
    },
    toggleUnderline() {
      this.textDecoration = this.textDecoration === "underline" ? "none" : "underline";
    },
    changeTextColor(color) {
      this.textColor = color;
    },
    changeFontSize(size) {
      this.fontSize = size;
    },
    changeFontFamily(font) {
      this.fontFamily = font;
    }
  },
  watch: {
    inputText(newValue, oldValue) {
      console.log("Nilai input berubah:", newValue);
    },
  },
};
</script>

<style>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #dedede;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  transform: translateX(5%);
}

.title {
  font-family: Georgia, "Times New Roman", Times, serif;
  text-align: center;

}

.form-container {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

.form-container p {
  font-family: sans-serif;
}

.text-input {
  width: 95%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: border-color 0.3s ease;
  word-wrap: break-word;
}

.text-input:focus {
  border-color: #2f8e28;
}

.highlight {
  background-color: yellow;
}

p {
  margin: 10px 0;
  color: #555;
}

.wrapped-text {
  display: block;
  max-width: 100%;
  overflow-wrap: break-word;
  font-family: "Courier New", Courier, monospace;
}

.option-group {
  margin-top: 20px;
}

.option-group p {
  font-weight: bold;
}

.option-group button {
  margin-right: 10px;
}

:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-color: #242424;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
