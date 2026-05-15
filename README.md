// Game Sederhana Tebak Gambar
// Jalankan di browser menggunakan file HTML

// Daftar gambar dan jawabannya
const dataGambar = [
  {
    gambar: "🍎",
    jawaban: "apel"
  },
  {
    gambar: "🐱",
    jawaban: "kucing"
  },
  {
    gambar: "🚗",
    jawaban: "mobil"
  },
  {
    gambar: "⚽",
    jawaban: "bola"
  }
];

let skor = 0;
let index = 0;

// Membuat tampilan game
document.body.innerHTML = `
  <div style="text-align:center; font-family:Arial;">
    <h1>Game Tebak Gambar</h1>
    <h2 id="gambar"></h2>

    <input type="text" id="jawaban" placeholder="Masukkan jawaban">
    <button onclick="cekJawaban()">Jawab</button>

    <p id="hasil"></p>
    <p id="skor">Skor: 0</p>
  </div>
`;

// Menampilkan gambar pertama
tampilkanGambar();

function tampilkanGambar() {
  if (index < dataGambar.length) {
    document.getElementById("gambar").innerText =
      dataGambar[index].gambar;
  } else {
    document.body.innerHTML = `
      <div style="text-align:center; font-family:Arial;">
        <h1>Game Selesai!</h1>
        <h2>Skor Akhir: ${skor}</h2>
      </div>
    `;
  }
}

function cekJawaban() {
  const input = document.getElementById("jawaban").value.toLowerCase();
  const hasil = document.getElementById("hasil");

  if (input === dataGambar[index].jawaban) {
    hasil.innerText = "Benar!";
    skor++;
  } else {
    hasil.innerText =
      "Salah! Jawaban yang benar: " +
      dataGambar[index].jawaban;
  }

  document.getElementById("skor").innerText = "Skor: " + skor;

  document.getElementById("jawaban").value = "";

  index++;
  setTimeout(tampilkanGambar, 1000);
}
