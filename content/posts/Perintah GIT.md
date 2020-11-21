---
author: "Deni Gunawan"
date: 2020-11-06
linktitle: Belajar Git
title: Belajar Git
categories: [ "Linux", "CLI", "Kali Linux", "ubuntu" ]
tags: ["Linux", "CLI", "Kali Linux", "command liine"]
weight: 10
---
## INSTALL GIT
	sudo apt install git 

## Check Version
	git --version 

## Konfigurasi awal
	git config --global user.name "DeniGunawan" // bersifat wajib
	git config --global user.email "artdengun@gmail.com" // wajib sama dengan git akun kita

## check konfigurasi git 
		git --list 

## membuat repository 
		git init project-1 // nama project sesuai dengan kebutuhan

## membuat working directory
		git init . // perintah ini digunakan untuk membuat folder menjadi working directory

## membuat repository pada direktory
		git init /var/www/html/proyekweb // membuat repository pada git 

## Melihat Status Repository
		git status 

## mengubah kondisi file dari modified dan staged 
		git add nama_file. 

		git add *.html // mengubah semua file yang berektensi .html 
		
		git add . // mengubah semua file yang ada di directory working

## mengubah kondisi file dari staged ke commited
		git commit -m " catatan yang direvisi " // -m artinya argumen

## Melihat catatan perubah pada repository 
		git log 
		
		git log --oneline // melihat log yang lebih pendek

## Melihat log pada nomer revisi 
		git log cf08ca0837cf26f1c595be36bb3a6b815e311be1 // nomer revisi sesuai number yang kita cari

## Melihat log pada file tertentu 
		git log index.html // file di tentukan sesuai yang kita cari

## Melihat log Revisi oleh author tertentu 
		git log --author='deni gunawan' // nama author disesuaikan oleh member yang terkoneksi dengan repo

## Melihat perbandingan perubahan yang dilakukan pada revisi 
		git diff cf08ca0837cf26f1c595be36bb3a6b815e311be1 // nomer revisi disesuiakana dengan kebutuhan

		(+) artinya kode yang ditambahkan
		(-) simbolnya akan menggunakan minus

		git diff akan membandingkan perubahan yang baru saja dilakukan dengan revisi/commit terakhir.

## Melihat perbandingan pada file 
		git diff index.html // melihat perbandingan pada file

## Melihat Perbandingan antar Revisi/Commit
		// git diff <nomer commit> <nomer commit> 
		git diff cf08ca0837cf26f1c595be36bb3a6b815e311be1 06f735af7724558164c87f6b1ce3ca7778eb1c1b 

## Perbandingan Antar Cabang (Branch)
		git diff <nama cabang> <nama cabang>

## Membatalkan Perubahan pada revisi ( modified,   sebelum di stage dan commit)
		git checkout nama_file.html // nama file disesuaikan dengan kebutuhan

## Membatalkan Perubahan File yang Sudah dalam Kondisi staged 
		git reset index.html // nama file di sesuaikan dengan kebutuhan , jika file ini dijalankan maka file yang 			// kita reset akan kembali keposisi modified, untuk membatalkan perubahan sebelumnya pada modified gunakan 			// perintah git checkout 

## Membatalkan Perubahan File yang Sudah dalam Kondisi Commited

	git checkout b05f7d05c9298f2cd11b870369f3cf4b2350eca7 index.html
	git reset index.html

## Kembali ke 3 Commit sebelumnya 
	git checkout HEAD~3 index.html
	
## Membatalkan Semua Perubahan yang ada
	git revert -n <nomer commit>

## Cara Membuat Cabang Baru 
	git branch fitur_registrasi // pembuatan cabang baru 

## Melihat Cabang apa saja yang terdapat di repo
	git branch // tnda * berarti cabang yang sedang aktif / kita ada disana


-- Penjelasan
	Repository adalah gudang / tempat penyimpanan proyek kita
	
	.git di dalam proyek kita. Direktori ini digunakan Git sebagai database 
	untuk menyimpan perubahan yang kita lakukan. WARNING!! jika direktory .git terhapus
	maka semua rekam jejak/catatan akan hilang

	.gitignore adalah merupakan sebuah file yang berisi daftar nama-nama file dan direktori yang akan diabaikan oleh 	  Git. Perubahan apapun yang kita lakukan terhadap file dan direktori yang sudah masuk ke dalam daftar .gitignore 		 tidak akan dicatat oleh Git.


	3 Kondisi File di GIT
		
		- Modified adalah kondisi dimana revisi atau perubahan sudah dilakukan, tetapi belum ditandai dan belum 		  disimpan di version control

		- Staged adalah kondisi dimana revisi sudah ditandai, tetapi belum disimpan di version control. Untuk 			  mengubah kondisi file dari modified ke staged gunakan perintah git add nama_file. 

		- Commited adalah kondisi dimana revisi sudah disimpan di version control. perintah untuk mengubah kondisi 			  file dari staged ke commited adalah git commit.

	git log berfungsi untuk melihat history log

	git diff berfungsi untuk melihat perbedaan perubahan revisi 

	Kondisi staged merupakan kondisi file yang sudah di add (git add), namun belum disimpan (git commit) ke dalam Git.

		