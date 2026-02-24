<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes">
    <title>URICA – Fokus Rehabilitasi</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: #aaa;
            font-family: 'Times New Roman', Times, serif;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding: 10px;
        }
        .kertas {
            max-width: 1400px;
            width: 100%;
            background: white;
            border: 1px solid black;
            padding: 20px 15px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }
        /* Kop tanpa logo – teks pusat */
        .kop {
            text-align: center;
            border-bottom: 2px solid black;
            padding-bottom: 15px;
            margin-bottom: 25px;
        }
        .kop .lembaga {
            font-size: 26px;
            font-weight: bold;
            letter-spacing: 1.2px;
            text-transform: uppercase;
            margin: 0 0 5px 0;
            line-height: 1.2;
        }
        .kop .alamat {
            font-family: 'Courier New', Courier, monospace;
            font-size: 13px;
            margin: 6px auto 8px auto;
            padding: 5px 0;
            border-top: 1px dotted black;
            border-bottom: 1px dotted black;
            max-width: 800px;
        }
        .kop .judul-kuesioner {
            font-size: 18px;
            font-weight: normal;
            text-transform: uppercase;
            margin: 0;
        }

        .identitas {
            display: flex;
            flex-wrap: wrap;
            gap: 15px 20px;
            border: 1px solid black;
            padding: 15px 20px;
            margin-bottom: 25px;
            background: #f9f9f9;
            justify-content: center;
        }
        .field {
            display: flex;
            align-items: center;
            gap: 5px;
            flex-wrap: wrap;
        }
        .field label {
            font-weight: bold;
            min-width: 70px;
        }
        .field input {
            border: 1px solid black;
            padding: 6px 8px;
            font-family: inherit;
            background: white;
            min-width: 150px;
            font-size: 14px;
        }
        .date-input, .time-input {
            width: 160px;
        }

        .instruksi-wawancara {
            margin-bottom: 30px;
            padding: 15px;
            border: 1px solid black;
            background: #f2f2f2;
            font-size: 15px;
            text-align: justify;
        }
        .instruksi-wawancara p {
            margin-bottom: 8px;
        }
        .instruksi-wawancara .judul-instruksi {
            font-weight: bold;
            text-transform: uppercase;
            border-bottom: 1px solid black;
            padding-bottom: 5px;
            margin-bottom: 10px;
        }

        .bagian-judul {
            font-weight: bold;
            margin: 40px 0 12px 0;
            font-size: 16px;
            border-bottom: 1px solid black;
            padding-bottom: 5px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            clear: both;
        }

        .tabel-container {
            margin-bottom: 40px;
            border: 1px solid black;
            background: white;
            overflow-x: auto;
            page-break-inside: avoid;
            -webkit-overflow-scrolling: touch;
        }
        table {
            border-collapse: collapse;
            width: 100%;
            font-size: 13px;
            min-width: 950px;  /* cukup lebar untuk skala panjang */
        }
        th {
            border: 1px solid black;
            padding: 8px 2px;
            background: #e0e0e0;
            font-weight: bold;
            text-align: center;
            vertical-align: middle;
        }
        /* Kolom nomor dan pernyataan */
        th:nth-child(1) { width: 40px; }
        th:nth-child(2) { width: auto; }
        /* Kolom skala (3-7) */
        th:nth-child(n+3) {
            width: 90px;
            font-size: 12px;
            line-height: 1.2;
        }
        .skala-panjang {
            font-size: 9px;
            font-weight: normal;
            display: block;
            margin-top: 5px;
            word-break: break-word;
            white-space: normal;
        }
        td {
            border: 1px solid black;
            padding: 8px 2px;
            vertical-align: middle;
            text-align: center;
        }
        td:first-child {
            text-align: center;
            font-weight: bold;
            background: #f2f2f2;
            width: 40px;
        }
        td:nth-child(2) {
            text-align: left;
            padding-left: 8px;
        }
        .radio-cell {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .radio-cell input[type="radio"] {
            transform: scale(1.2);
            margin: 0;
            cursor: pointer;
        }

        /* Hasil skoring */
        .hasil-skoring {
            margin: 35px 0 20px;
            border: 2px solid black;
            padding: 18px;
            background: #ffffff;
            page-break-inside: avoid;
        }
        .hasil-skoring h4 {
            margin: 0 0 20px 0;
            text-align: center;
            font-weight: bold;
            text-decoration: underline;
            font-size: 18px;
        }
        .grid-skor {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
        }
        .kartu-skor {
            border: 1px solid black;
            padding: 12px 15px;
            min-width: 160px;
            background: #f2f2f2;
            text-align: center;
        }
        .kartu-skor p { margin: 6px 0; }
        .skor-angka { font-weight: bold; font-size: 20px; }
        .readiness {
            background: #e6e6e6;
            font-size: 18px;
            padding: 10px;
            border: 1px solid black;
        }
        .catatan-interpretasi {
            font-size: 13px;
            margin-top: 15px;
            text-align: center;
            border-top: 1px solid black;
            padding-top: 12px;
            background: #f9f9f9;
            padding: 10px;
        }
        .catatan-interpretasi span {
            background: #ddd;
            padding: 3px 8px;
            margin: 0 5px;
            border: 1px solid black;
            font-weight: bold;
        }

        .tombol-aksi {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 30px 0 20px;
            flex-wrap: wrap;
        }
        .btn {
            border: 2px solid black;
            background: white;
            color: black;
            padding: 12px 30px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
            text-transform: uppercase;
        }
        .btn:hover { background: black; color: white; }

        footer {
            margin-top: 25px;
            font-size: 13px;
            text-align: center;
            border-top: 2px solid black;
            padding-top: 15px;
        }
        .kredit { font-style: italic; font-weight: bold; }

        /* Responsif untuk layar kecil */
        @media (max-width: 600px) {
            .identitas .field {
                width: 100%;
            }
            .field input {
                width: 100%;
            }
            .btn {
                width: 100%;
                text-align: center;
            }
        }

        @media print {
            @page {
                size: A4 landscape;
                margin: 1cm;
            }
            body {
                background: white;
                padding: 0;
                margin: 0;
            }
            .kertas {
                border: none;
                box-shadow: none;
                padding: 0.5cm;
                max-width: 100%;
            }
            .btn, .tombol-aksi {
                display: none;
            }
            .identitas input {
                border: none;
                background: transparent;
                border-bottom: 1px solid black;
            }
            .identitas {
                background: none;
                border: 1px solid black;
            }
            th {
                background: #ddd !important;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
            td:first-child {
                background: #f2f2f2 !important;
                -webkit-print-color-adjust: exact;
            }
            .tabel-container, .hasil-skoring {
                page-break-inside: avoid;
            }
            table {
                font-size: 11px;
            }
            td {
                padding: 4px 2px;
            }
        }
    </style>
</head>
<body>
<div class="kertas" id="kertasKuesioner">

    <!-- KOP TANPA LOGO (telah dirapikan) -->
    <div class="kop">
        <div class="kop-text">
            <div class="lembaga">FOKUS REHABILITASI NARKOTIKA INDONESIA</div>
            <div class="alamat">Jl. Riwayat 1 Gg Pertanian, Marindal Satu, Kec. Patumbak, Kabupaten Deli Serdang, Sumatera Utara 20148</div>
            <div class="judul-kuesioner">URICA (University of Rhode Island Change Assessment)</div>
        </div>
    </div>

    <!-- IDENTITAS DENGAN WAKTU -->
    <div class="identitas">
        <div class="field">
            <label>Nama Klien :</label>
            <input type="text" id="namaKlien" placeholder="(diisi klien)" style="width:220px;">
        </div>
        <div class="field">
            <label>Petugas :</label>
            <input type="text" id="petugas" placeholder="Nama petugas" style="width:170px;">
        </div>
        <div class="field">
            <label>Tanggal :</label>
            <input type="date" id="tanggal" class="date-input" value="2025-03-01">
        </div>
        <div class="field">
            <label>Waktu :</label>
            <input type="time" id="waktu" class="time-input" value="09:00">
        </div>
    </div>

    <!-- INSTRUKSI WAWANCARA -->
    <div class="instruksi-wawancara">
        <div class="judul-instruksi">PENGANTAR WAWANCARA</div>
        <p>Kuesioner ini mengukur kesiapan untuk berubah. Pewawancara membacakan setiap pernyataan, dan klien diminta memilih salah satu angka dari 1 sampai 5 yang paling sesuai dengan perasaannya saat ini.</p>
        <p><strong>Skala:</strong> 1 = Sangat Tidak Setuju, 2 = Tidak Setuju, 3 = Netral, 4 = Setuju, 5 = Sangat Setuju.</p>
        <p>Jawablah dengan jujur berdasarkan perasaan Anda sekarang. Hasil akan dihitung secara otomatis.</p>
    </div>

    <!-- TABEL URICA 32 ITEM -->
    <div class="bagian-judul">✦ Daftar Pernyataan</div>
    <div class="tabel-container">
        <table id="urica-table">
            <thead>
                <tr>
                    <th>No</th>
                    <th>Pernyataan</th>
                    <th>1<br><span class="skala-panjang">Sangat Tidak Setuju</span></th>
                    <th>2<br><span class="skala-panjang">Tidak Setuju</span></th>
                    <th>3<br><span class="skala-panjang">Netral</span></th>
                    <th>4<br><span class="skala-panjang">Setuju</span></th>
                    <th>5<br><span class="skala-panjang">Sangat Setuju</span></th>
                </tr>
            </thead>
            <tbody id="urica-body">
                <!-- diisi oleh javascript -->
            </tbody>
        </table>
    </div>

    <!-- HASIL SKORING -->
    <div class="hasil-skoring" id="hasilSkoring">
        <h4>SKOR PER SUBSCALE & READINESS</h4>
        <div class="grid-skor" id="skorGrid">
            <!-- hasil perhitungan ditampilkan di sini -->
        </div>
        <div class="catatan-interpretasi">
            <p><span>INTERPRETASI & RUMUS</span></p>
            <p><strong>Precontemplation (P):</strong> rendah = siap berubah, tinggi = belum siap.</p>
            <p><strong>Contemplation (C), Action (A), Maintenance (M):</strong> tinggi = lebih terlibat dalam tahap tersebut.</p>
            <p><strong>Rumus Readiness = (C + A + M) - P</strong> (menggunakan total skor masing-masing subskala). Semakin positif, semakin siap berubah.</p>
            <p><em>Catatan: Skor yang ditampilkan adalah jumlah total item per subskala (bukan rata-rata).</em></p>
        </div>
    </div>

    <!-- TOMBOL CETAK / PDF -->
    <div class="tombol-aksi">
        <button class="btn" id="cetakBtn">🖨️ CETAK / SIMPAN PDF</button>
    </div>

    <!-- Kredit pengembang (sesuai permintaan) -->
    <footer>
        <div class="kredit">Digitalisasi dokumen oleh <strong>Khairul Hafizin</strong></div>
        <div style="margin-top:5px;">FOKUS REHABILITASI NARKOTIKA INDONESIA – Deli Serdang</div>
    </footer>
</div>

<script>
(function() {
    // 32 item URICA dengan subskala: P, C, A, M
    const items = [
        { text: "Menurut saya, saya tidak punya masalah yang perlu diubah.", sub: "P" },
        { text: "Saya rasa tidak ada gunanya membicarakan masalah saya.", sub: "P" },
        { text: "Saya sudah berpikir bahwa saya mungkin ingin memperbaiki diri, tetapi belum siap.", sub: "P" },
        { text: "Saya mungkin menjadi bagian dari masalah, tetapi saya tidak benar-benar berpikir demikian.", sub: "P" },
        { text: "Saya tidak mau mengubah kebiasaan saya.", sub: "P" },
        { text: "Membicarakan masalah saya akan sia-sia.", sub: "P" },
        { text: "Saya ragu bahwa saya perlu berubah.", sub: "P" },
        { text: "Saya masih bertanya-tanya apakah saya memang perlu berubah.", sub: "P" },
        { text: "Saya pikir saya mungkin siap untuk memperbaiki diri.", sub: "C" },
        { text: "Saya berharap dapat lebih memahami diri saya sendiri.", sub: "C" },
        { text: "Saya ingin mencapai perubahan, tetapi tidak sendirian.", sub: "C" },
        { text: "Saya berharap seseorang akan memberi saya petunjuk untuk menyelesaikan masalah.", sub: "C" },
        { text: "Mungkin saya akan mau berkonsultasi dengan ahli.", sub: "C" },
        { text: "Saya berharap dapat lebih mengenal diri sendiri.", sub: "C" },
        { text: "Saya memiliki masalah dan saya benar-benar harus mengatasinya.", sub: "C" },
        { text: "Saya serius ingin berubah.", sub: "C" },
        { text: "Saya akhirnya melakukan sesuatu untuk mengatasi masalah saya.", sub: "A" },
        { text: "Saya secara aktif mengubah diri saya.", sub: "A" },
        { text: "Saya bekerja keras untuk berubah.", sub: "A" },
        { text: "Saya telah mulai mengatasi masalah saya, tetapi saya ingin bantuan.", sub: "A" },
        { text: "Saya telah mengambil tindakan untuk berubah.", sub: "A" },
        { text: "Saya sibuk mencoba memperbaiki diri.", sub: "A" },
        { text: "Saya telah mengubah beberapa kebiasaan, tetapi masih perlu bantuan.", sub: "A" },
        { text: "Saya sedang berusaha mengubah diri.", sub: "A" },
        { text: "Saya khawatir jika saya kambuh ke masalah lama.", sub: "M" },
        { text: "Saya mungkin butuh dorongan untuk mempertahankan perubahan.", sub: "M" },
        { text: "Saya telah berubah dan saya mencari cara agar tidak kambuh.", sub: "M" },
        { text: "Saya bekerja untuk mempertahankan kemajuan saya.", sub: "M" },
        { text: "Saya telah berhasil mengubah, tetapi saya tidak yakin dapat bertahan.", sub: "M" },
        { text: "Saya menjaga perubahan yang telah saya buat.", sub: "M" },
        { text: "Saya berusaha keras untuk mencegah kambuh.", sub: "M" },
        { text: "Saya telah mengubah dan saya menikmati hasilnya.", sub: "M" }
    ];

    // Fungsi membuat sel radio
    function createRadioCell(name, value) {
        return `<div class="radio-cell"><input type="radio" name="${name}" value="${value}"></div>`;
    }

    // Isi tabel
    function populateTable() {
        const tbody = document.getElementById('urica-body');
        tbody.innerHTML = '';
        items.forEach((item, index) => {
            let tr = document.createElement('tr');
            // No
            let tdNo = document.createElement('td');
            tdNo.textContent = index + 1;
            tr.appendChild(tdNo);
            // Pernyataan
            let tdText = document.createElement('td');
            tdText.textContent = item.text;
            tr.appendChild(tdText);
            // 5 kolom radio (nilai 1-5)
            for (let v = 1; v <= 5; v++) {
                let td = document.createElement('td');
                td.innerHTML = createRadioCell(`item_${index}`, v);
                tr.appendChild(td);
            }
            tbody.appendChild(tr);
        });
    }

    // Ambil nilai satu item
    function getItemValue(index) {
        const radios = document.getElementsByName(`item_${index}`);
        for (let r of radios) {
            if (r.checked) return parseInt(r.value, 10);
        }
        return null; // tidak diisi
    }

    // Hitung total skor tiap subskala
    function hitungSkor() {
        let sumP = 0, sumC = 0, sumA = 0, sumM = 0;
        let countP = 0, countC = 0, countA = 0, countM = 0;

        items.forEach((item, idx) => {
            let val = getItemValue(idx);
            if (val !== null) {
                if (item.sub === 'P') { sumP += val; countP++; }
                else if (item.sub === 'C') { sumC += val; countC++; }
                else if (item.sub === 'A') { sumA += val; countA++; }
                else if (item.sub === 'M') { sumM += val; countM++; }
            }
        });

        // Tampilkan total (bisa juga rata-rata, tapi biasanya total)
        let totalP = countP > 0 ? sumP : 0;
        let totalC = countC > 0 ? sumC : 0;
        let totalA = countA > 0 ? sumA : 0;
        let totalM = countM > 0 ? sumM : 0;
        let readiness = (totalC + totalA + totalM) - totalP;

        return {
            P: totalP,
            C: totalC,
            A: totalA,
            M: totalM,
            readiness: readiness
        };
    }

    // Perbarui tampilan skor
    function updateSkor() {
        let skor = hitungSkor();
        let html = `
            <div class="kartu-skor">
                <p><strong>Precontemplation (P)</strong></p>
                <p class="skor-angka">${skor.P}</p>
            </div>
            <div class="kartu-skor">
                <p><strong>Contemplation (C)</strong></p>
                <p class="skor-angka">${skor.C}</p>
            </div>
            <div class="kartu-skor">
                <p><strong>Action (A)</strong></p>
                <p class="skor-angka">${skor.A}</p>
            </div>
            <div class="kartu-skor">
                <p><strong>Maintenance (M)</strong></p>
                <p class="skor-angka">${skor.M}</p>
            </div>
            <div class="kartu-skor readiness">
                <p><strong>Readiness Score</strong></p>
                <p class="skor-angka">${skor.readiness}</p>
            </div>
        `;
        document.getElementById('skorGrid').innerHTML = html;
    }

    // Inisialisasi event listener untuk setiap radio
    function initRadios() {
        const allRadios = document.querySelectorAll('input[type="radio"]');
        for (let r of allRadios) {
            r.addEventListener('change', updateSkor);
        }
    }

    // Fungsi untuk tombol cetak
    function setupCetak() {
        document.getElementById('cetakBtn').addEventListener('click', function() {
            window.print();
        });
    }

    // Menjalankan inisialisasi setelah halaman dimuat
    window.addEventListener('load', function() {
        populateTable();        // isi tabel dengan item
        initRadios();           // pasang event listener ke semua radio
        updateSkor();           // hitung skor awal (akan 0 semua karena belum ada pilihan)
        setupCetak();           // aktifkan tombol cetak
    });
})();
</script>
</body>
</html>
