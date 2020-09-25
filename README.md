## Tentang

Boilerplate untuk landing page ISE 2020. Menggunakan [parcel](https://parceljs.org/) sebagai bundler. Plugin parcel yang dipakai meliputi :

- autoprefixer, digunakan untuk memberikan prefix pada style css agar kompatibel dengan browser - browser yang didefinisikan pada konfigurasi `.browserlistrc`. Konfigurasi terletak pada `postcssrc` dan `.browserlistrc`.
- parcel-plugin-custom-dist-structure, digunakan untuk mengatur struktur directory assets. Konfigurasi terdapat pada `package.json`.
- parcel-plugin-purgecss, digunakan untuk menghapus style css yang tidak digunakan, sehingga setelah dibundle css manjadi lebih ramping. Konfigurasi terdapat pada `purgecss.config.js`.
- postcss-modules, memungkinkan parcel untuk menggunakan modul postcss (seperti autoprefixer diatas). Konfigurasi terdapat pada `.postcssrc`.

## Pemasangan

```bash
git clone https://github.com/rochimfn/boilerplate-landing-page.git
cd boilerplate-landing-page
```

Jika menggunakan yarn (direkomendasikan)

```
yarn add
```

Jika menggunakan npm.

```
npm install
```

## Konfigurasi

### HTML

Semua file `.html` yang digunakan perlu dikonfigurasikan pada file `package.json` agar parcel tahu mana saja file `.html` yang perlu dibundling.

Contoh konfigurasi.

```json
"start": "parcel serve src/index.html", # tambahkan kesini
"build": "parcel build src/index.html", # kesini
"watch": "parcel watch src/index.html"  # dan kesini
```

### CSS

Boilerplate ini secara default menggunakan framework css bootstrap dan menggunakan font awesome. Konfigurasi css dan font yang akan dipakai terletak pada `src/assets/css/main.css`.

Contoh konfigurasi.

```css
# jika menggunakan seluruh style bootstrap
@import "bootstrap/dist/css/bootstrap.css";

# jika menggunakan bootstrap grid saja
@import "bootstrap/dist/css/bootstrap-grid.css";

# jika menggunakan seluruh paket font awesome
@import "@fortawesome/fontawesome-free/css/all.css";

# jika menggunakan google fonts
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap");
```

Konfigurasi purgecss dengan mengisikan daftar file `.html` yang menggunakan css pada bagian _content_ dalam file `purgecss.config.js`, serta file `.css` yang dipakai pada bagian _css_.

Contoh konfigurasi.

```javascript
module.exports = {
  content: ["src/index.html", "src/about/index.html", "src/faq/*.html"],
  css: ["src/assets/css/main.css", "src/assets/css/custom.css"],
};
```

Konfigurasi autoprefixer css pada file `.browserlistrc` dengan mengisikan opsi yang didukung, dapat dilihat di [https://github.com/browserslist/browserslist](https://github.com/browserslist/browserslist).

Contoh konfigurasi.

```conf
# mendukung 2 versi browser terakhir
last 2 versions

# menggunakan opsi default
defaults
```

### JS

Secara default boilerplate ini menggunakan `bootstrap`, `jquery` dan `popper.js`. Konfigurasi terdapat pada `src/assets/js/main.js`.

Contoh konfigurasi.

```javascript
# jika menggunakan javascript bawaan bootstrap
import "bootstrap";
```

## Perintah konsol

### Daftar perintah

Jika menggunakan yarn

```
yarn start
yarn build
yarn watch
```

Jika menggunakan npm

```
npm start
npm build
npm watch
```

### Penjelasan perintah

`start` setelah perintah ini dijalankan parcel akan membundling html, css, js dan asset lain lalu menempatkan outputnya pada directory `dist`. Setelah proses bundling selesai parcel akan menjalankan web server yang mengarah pada directory `dist`. Akses terdapat web server akan ditampilkan pada konsol (terminal). **Pada mode ini, seluruh file css dan js akan di sediakan apa adanya tanpa ada minifikasi atau penghapusan.**

`watch` setelah perintah ini dijalankan parcel akan membundling html, css, js dan asset lain lalu menempatkan outputnya pada directory `dist` layaknya perintah `start` diatas. Namun web server tidak akan dijalankan. **Pada mode ini, seluruh file css dan js akan di sediakan apa adanya tanpa ada minifikasi atau penghapusan.**

`build` setelah perintah ini dijalankan parcel akan membundling html, css, js dan asset lain lalu menempatkan outputnya pada directory `dist`. Pada mode ini web server tidak akan dijalankan, parcel akan exit setelah build selesai. **Pada mode ini, seluruh file css dan js akan diminifikasi dan dilakukan penghapusan pada bagian yang tidak diperlukan.** Pastikan lakukan testing setelah build selesai sebelum deployment dilakukan.
