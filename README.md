# InventoryManagementSystem_PBO-VII_Kel2

IMPLEMENTASI KONSEP PEMROGRAMAN BERORIENTASI OBJEK UNTUK INVENTARIS MANAGEMENT SYSTEM MENGUNAKAN BAHASA PEMOGRAMAN PYTHON BERBASIS GRAFIK USER INTERFACE (GUI)


 
Disusun Oleh:
5220411323 Revaldo
5220411328 Muhamad Adin Musababa
5220411329 Amalia Nur Hanifah
5220411339 Achmad Risqi Arifudin
5220411343 Eko Fajrul Falah



1.	Pendahuluan
Bahasa pemograman python adalah Bahasa yang perkembangannya sangat pesat saaat ini. Karena bahasa peograman python yang open source dan banyak pengembangan librari yang memudahkan untuk pengembangan mengunakan bahasa python ini. Dari itu, python banyak digunakan dalam berbagai pengembangan teknoogi seperti Artivicial Intelegence, Data Science, Machine Learning, pembuatan websait dan masih banyak lainnya. 
Dalam pengembangannya python juga digunakan dalam pengembangan Object Oriented Programing (OOP). dalam pengembangan sistem mengunakan OOP python struktur programnya hampir sama dengan bahasa Objeck lainnya seperti Java, C, dll. 
GUI adalah singkatan dari Graphical User Interface, yang berarti antarmuka pengguna grafis. Ini adalah jenis antarmuka yang memungkinkan pengguna berinteraksi dengan perangkat elektronik melalui elemen visual seperti ikon, tombol, jendela, menu, dan gambar, bukan hanya teks. GUI menjadi cara utama untuk berinteraksi dengan komputer, smartphone, tablet, dan berbagai perangkat elektronik lainnya. 
Pengelolaan inventaris yang akurat dan efisien merupakan aspek krusial dalam operasional berbagai instansi dan perusahaan. Pendekatan OOP menawarkan modularitas, reusability, dan kemudahan pemeliharaan code menjadikan solusi untuk pengebangan sistem yang kompleks. Dengan penjelasan dari python diatas menjadikan python sebagai fondasi yang kuat untuk pengembangan sistem berbasis OOP, dan dengan digabungkan degan GUI yang intuitif dapat meningkatkan user experience dan memudahkan interaksi dengan sistem, sehingga meningkatkan efektivitas pengelolaan inventaris.
Dalam pembuatan sistem ini akan difokuskan pada bagaimana merancang dan mengimpelementasikan sistem inventaris management yang tersetruktur, dan mudah dipelihara dengan pengabungan OOP dan GUI dengan bahasa pemograman python yang bertujuan untuk mengembangkan sistem inventaris management berbasis OOP dan GUI menggunakan Python untuk meningkatkan efektivitas pengelolaan inventaris dan kemudahan penggunaan dan memberikan solusi yang efektif untuk pengelolaan inventaris yang lebih akurat, efisien, dan mudah digunakan .
2.	Metode
Dalam pembuatan sitem inventaris ini, akan di buat dengan bahasa pemograan python dan visual studio code sebagai tools developent-nya. Karena sistem ini akan dibagun berbasis GUI untuk mempermudah pembuatannya akan digunakan library Tkinter. 
Langkah awal pembuatanya dalah dengan import library Tkinter.
import tkinter as tk
from tkinter import messagebox
setelah library Tkinter teruat dalam baris program, akan dibuat sebuah Class digunakan menampung atribut dan metod yang dari Item barang inventoris di perusahaan. 
class Item:
    def __init__(self, item_id, nama, quantity, price):
        self.item_id = item_id
        self.nama = nama
        self.quantity = quantity
        self.price = price
Kelas ini digunakan untuk merepresentasikan setiap item dalam inventaris seperti id barang, nama barang, jumlah barang, dan harga saat pebeliah barang. Progra ini di bungkus dalam fungsi __init__ yang memangil dirinya sendiri untuk menjalankannya. 
Setelah class yang digunakan untuk menapung item barang jadi, maka akan dibuat program di dalam class InventoryApp. Class inilah yang bertangung jawab atas antarmuka pengguna dan operasi-operasi pada inventaris.
class InventoryApp:
    def __init__(self, window):
        self.window = window
        self.window.title("Inventory Management System")
        self.items = []

        # Item ID
        self.item_id_label = tk.Label(self.window, text="Item ID")
        self.item_id_label.grid(row=0, column=0)
        self.item_id_entry = tk.Entry(self.window)
        self.item_id_entry.grid(row=0, column=1)

        # Nama
        self.nama_label = tk.Label(self.window, text="Nama")
        self.nama_label.grid(row=1, column=0)
        self.nama_entry = tk.Entry(self.window)
        self.nama_entry.grid(row=1, column=1)

        # Quantity
        self.quantity_label = tk.Label(self.window, text="Quantity")
        self.quantity_label.grid(row=2, column=0)
        self.quantity_entry = tk.Entry(self.window)
        self.quantity_entry.grid(row=2, column=1)

        # Price
        self.price_label = tk.Label(self.window, text="Harga")
        self.price_label.grid(row=3, column=0)
        self.price_entry = tk.Entry(self.window)
        self.price_entry.grid(row=3, column=1)

        # Add Button
        self.add_button = tk.Button(self.window, text="Add",     command=self.add_item)
        self.add_button.grid(row=4, column=0)

        # Update Button
        self.update_button = tk.Button(self.window, text="Update", command=self.update_item)
        self.update_button.grid(row=4, column=1)

        # Delete Button
        self.delete_button = tk.Button(self.window, text="Delete", command=self.delete_item)
        self.delete_button.grid(row=5, column=0)

        # Clear Button
        self.clear_button = tk.Button(self.window, text="Clear", command=self.clear_fields)
        self.clear_button.grid(row=5, column=1)

        # Listbox
        self.listbox = tk.Listbox(self.window, width=40)
        self.listbox.grid(row=6, column=1, rowspan=10)

        header_text = "Item ID\t    Nama\t    Quantity\t    Harga"  
        self.listbox.insert(tk.END, header_text)   
code pada class diatas akan mendisain tampilan intervace user. Dan tampilan ini akan dihubungkan pada fungsi sesuai dengan tombol yang di klik oleh user sesuai dengan fitur. Fitur-fitur tersebut ntara lain:
1.	Menambahkan item 
    def add_item(self):
        item_id = self.item_id_entry.get()
        nama = self.nama_entry.get()
        quantity = self.quantity_entry.get()
        price = self.price_entry.get()

        new_item = Item(item_id, nama, quantity, price)
        self.items.append(new_item)
        self.listbox.insert(tk.END, f"   {item_id}           {nama}          {quantity}         {price}")
        self.clear_fields()

fungsi diatas akkan diproses ketika user telah melakukan pengisian form yang telah dibuat sebelumnya. Form yang telah diisi oleh user ketika user menekan tombol add aitem maka item tersebut otomatis akan asuk ke dalam list yang telah di definisikan sebelumnya. 
2.	Update item
    def update_item(self):
        item_id = self.item_id_entry.get()
        nama = self.nama_entry.get()
        quantity = self.quantity_entry.get()
        price = self.price_entry.get()

        for item in self.items:
            if item.item_id == item_id:
                item.nama = nama
                item.quantity = quantity
                item.price = price

        self.listbox.delete(0, tk.END)
        for item in self.items:
            self.listbox.insert(tk.END, f"{item.item_id}    {item.nama}     {item.quantity}     {item.price}")
        self.clear_fields()
	fungsi ini akan memproses pengubahan item berdassarkan id yang telah di tambahkan sebelumnya. Jika item tidak ditemukan maka proses tidak bisa dilakukan. Jika item diteukan, item akan dirubah sesuai dengan form yang telah diisikan user untuk mengubah.
3.	Delete item
    def delete_item(self):
        item_id = self.item_id_entry.get()

        for item in self.items:
            if item.item_id == item_id:
                self.items.remove(item)
                break

        self.listbox.delete(0, tk.END)
        for item in self.items:
            self.listbox.insert(tk.END, f"{item.item_id}    {item.nama}     {item.quantity}     {item.price}")
        self.clear_fields()
fungsi ini akan dijankan ketika user ingin menghapus item barang yang telah dimasukkan. Fungsi ini juga akan menghapus seuai dengan id item.
3.	Hasil dan pembahasan
Setelah kedua class terdefinisikan, selanjutnya kita bisa menjalakan program dengan perintah berikut:
root = tk.Tk()
sistem = InventoryApp(root)
root.mainloop()
code diatas menginisiasikan Tkinter pada fariable root, kemudian pada variable sistem akan menampung class InventoryApp dengan paraeternya adalah root, setelah itu program dijalankan dengan root.mainloop() sebagai perulangan pada root.
	Dari hasil penjalanan itu akan dihasilkan GUI dengan tampilan sebagai berikut:
 
	
	Gambar diatas merupakan hasil inisiasi dari pengabungan code pada metode, pada gambar tersebut terdapat from input untuk mengisi barang-barang yang akan direkap dalam sistem. Kolom item ID akan menampung nilai id dari barang yang digunakan sebagai kunci dari barang tersebut. Nama adalah nama barang yang akan direkap dalam sistem. Quantity adalah jumlah barang yang akan dimasukkan dalam sistem. Harga adalah penampung harga barang yang akan dimasukkan dalam sistem.
	Setealah mengisi from diatas dapat enekan tombol add yang akan menjalankan fungsi add_item pada code sebelumnya. Data yang telah diisikan akan ditampung dalam list yang tertera dibawah from. 
	Jika ingin mengubah barang, dapat menginputkan terlebih dahulu id barangnya, setelah itu ubah yang ingin diubah, seperti nama jumlah, dan harga.
	Jika inggin menghapus barang yang telah dinputkan, kita dapat en seleksi barang tersebut lalu tekan delete, ataupun dapat dengan inputkan terlebih dahulu item yang akan dihapus lalu tekan tombol delete.
