# Latihan_modul4
# Soal 1
Buat sebuah file sistem yang kamu buat ke /home/[user]/Downloads, lalu ubah nama file yang ada pada folder tersebut menjadi [nama file].[ekstensi].bak. File .bak tersebut hanya dapat dibaca.
Jawab :
- Jadi untuk mengerjakan ini kita hanya perlu mengopaskan kodingan yang ada pada modul di bagian yang dapat memodifikasi file system di userspace tanpa perlu mengubah kode yang ada pada kernel dan menggantinya rootnya dari Document menjadi Downloads
- Setelah itu kita menambahkan strcat pada whilenya 

      while ((de = readdir(dp)) != NULL) {
		    struct stat st;
		    memset(&st, 0, sizeof(st));
		    st.st_ino = de->d_ino;
		    st.st_mode = de->d_type << 12;
		    strcat(de->d_name, ".bak"); //berguna untuk menambahkan ekstensi ".bak"
		    res = (filler(buf, de->d_name, &st, 0));
			  if(res!=0) break;
	    }

# Soal 2
Buat sebuah file system yang mengarah ke /home/[user]/Documents. Pada saat membuka file dengan ekstensi .pdf, .doc, .txt pada direktori Documents akan muncul pesan error “Terjadi kesalahan! File berisi konten berbahaya.” dan tidak dapat membaca file tersebut. Setelah memunculkan pesan error, file tersebut diganti namanya menjadi <namafile>.<ekstensi>.ditandai. Setelah memunculkan pesan error dan mengganti nama file tadi, file tersebut otomatis dipindahkan ke direktori rahasia. Jika folder rahasia belum ada, maka secara otomatis akan membuat direktori “rahasia” sebelum dipindahkan dan file tidak bisa di read write execute.
Jawab :
  
