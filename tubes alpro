package main

import (
	"fmt"
	"math/big"
)

const MONTH = 12
const jumbarang = 1024

type AlatElektronik struct {
	kwh, total, biaya int
	jumlah, bulan     int
	barang            [jumbarang]string
	daya              [jumbarang]int
	waktu             [jumbarang]int
}

type arrayAlatElektronik [MONTH]AlatElektronik

func main() {
	tampilan()
}

func tampilan() {
	var option, n int
	var array arrayAlatElektronik
	for option != 8 {
		fmt.Println("[<>]=====================================================================[<>]")
		fmt.Println(" ||                 APLIKASI PENGHITUNG KONSUMSI ENERGI LISTRIK            ||")
		fmt.Println("[<>]=====================================================================[<>]")
		fmt.Println("1. Input penggunaan listrik")
		fmt.Println("2. Penggunaan konsumsi listrik terbesar dan terkecil")
		fmt.Println("3. Menampilkan penggunaan listrik tiap bulan")
		fmt.Println("4. Menampilkan penggunaan listrik pada bulan tertentu")
		fmt.Println("5. Menampilkan penggunaan listrik atau biaya dari yang terkecil hingga terbesar dalam setahun")
		fmt.Println("6. Membandingkan penggunaan listrik pada bulan tertentu")
		fmt.Println("7. Edit")
		fmt.Println("8. Exit")
		fmt.Println("Masukan pilihanmu: ")
		fmt.Scan(&option)

		if option == 1 {
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||                      INPUT PENGGUNAAN LISTRIK                         ||")
			fmt.Println("[<>]=====================================================================[<>]")
			input(&array, &n)
		} else if option == 2 {
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||                 PENGGUNAAN LISTRIK TERBESAR DAN TERKECIL              ||")
			fmt.Println("[<>]=====================================================================[<>]")
			maximum(array, n)
			minimum(array, n)
		} else if option == 3 {
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||                  MENAMPILKAN SEMUA PENGGUNAAN LISTRIK                 ||")
			fmt.Println("[<>]=====================================================================[<>]")
			printsemua(array, n)
		} else if option == 4 {
			var option int
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||                      PENCARIAN BERDASARKAN                            ||")
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println("1. Berdasarkan bulan")
			fmt.Println("2. Berdasarkan biaya")
			fmt.Println("3. Exit")
			fmt.Print("Masukan pilihanmu: ")
			fmt.Scan(&option)
			if option == 1 {
				var bulan int
				fmt.Print("Pada bulan: ")
				fmt.Scan(&bulan)
				printbulan(array, n, bulan)
			} else if option == 2 {
				var biaya int
				fmt.Print("Dengan biaya sebesar: ")
				fmt.Scan(&biaya)
				printbiaya(array, n, biaya)
			}
		} else if option == 5 {
			var option int
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||MENAMPILKAN PENGGUNAAN LISTRIK ATAU BIAYA DARI TERKECIL HINGGA TERBESAR||")
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println("1. Daya")
			fmt.Println("2. Biaya")
			fmt.Println("3. Exit")
			fmt.Print("Masukan pilihanmu: ")
			fmt.Scan(&option)
			if option == 1 {
				fmt.Println("[<>]=====================================================================[<>]")
				fmt.Println(" ||                MENAMPILKAN DAYA YANG SUDAH TERURUT                    ||")
				fmt.Println("[<>]=====================================================================[<>]")
				dayaterurut(array, n)
			} else {
				fmt.Println("[<>]=====================================================================[<>]")
				fmt.Println(" ||                MENAMPILKAN BIAYA YANG SUDAH TERURUT                   ||")
				fmt.Println("[<>]=====================================================================[<>]")
				biayaterurut(array, n)
			}
		} else if option == 6 {
			var bulan1, bulan2 int
			fmt.Print("Pada bulan ke: ")
			fmt.Scan(&bulan1)
			fmt.Print("Dengan bulan ke: ")
			fmt.Scan(&bulan2)
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||         MENAMPILKAN PENGGUNAAN LISTRIK YANG SUDAH DIBANDINGKAN        ||")
			fmt.Println("[<>]=====================================================================[<>]")
			banding(array, bulan1, bulan2)
		} else if option == 7 {
			var option int
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||                              EDIT                                     ||")
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println("1. Hapus barang")
			fmt.Println("2. Edit barang")
			fmt.Println("3. Exit")
			fmt.Print("Masukan pilihanmu: ")
			fmt.Scan(&option)
			if option == 1 {
				var bulan int
				var barang string
				fmt.Print("Pada bulan: ")
				fmt.Scan(&bulan)
				fmt.Println("Padda bulan", bulan, "terdapat barang:")
				for i := 0; i < array[bulan-1].jumlah; i++ {
					fmt.Println("Barang ke-", i+1, " Jenis:", array[bulan-1].barang[i])
				}
				fmt.Print("Barang yang akan dihapus: ")
				fmt.Scan(&barang)
				hapus(&array, bulan, barang)
			} else if option == 2 {
				var bulan int
				var barang string
				fmt.Print("Pada bulan: ")
				fmt.Scan(&bulan)
				fmt.Println("Padda bulan", bulan, "terdapat barang:")
				for i := 0; i < array[bulan-1].jumlah; i++ {
					fmt.Println("Barang ke-", i+1, " Jenis:", array[bulan-1].barang[i])
				}
				fmt.Print("Barang yang akan diedit: ")
				fmt.Scan(&barang)
				edit(&array, bulan, barang)
			}
		} else if option == 8 {
			fmt.Println("[<>]=====================================================================[<>]")
			fmt.Println(" ||             TERIMAKASIH SUDAH MENGGUNAKAN APLIKASI KAMI               ||")
			fmt.Println("[<>]=====================================================================[<>]")
		}
	}
}

func input(arr *arrayAlatElektronik, n *int) {
	var bulan int
	fmt.Print("Penggunaan energi listrik pada bulan: ")
	fmt.Scan(&bulan)

	fmt.Print("Jumlah barang elektronik: ")
	fmt.Scan(&arr[bulan-1].jumlah)
	arr[bulan-1].bulan = bulan
	fmt.Println("Barang elektronik:")
	for i := 0; i < arr[bulan-1].jumlah; i++ {
		fmt.Println("Barang ke-", i+1)
		fmt.Print("Jenis: ")
		fmt.Scan(&arr[bulan-1].barang[i])
		fmt.Print("Daya (Watt): ")
		fmt.Scan(&arr[bulan-1].daya[i])
		fmt.Print("Penggunaan rata-rata dalam sehari (Jam): ")
		fmt.Scan(&arr[bulan-1].waktu[i])
	}
	fmt.Print("Total penggunaan listrik pada bulan ", bulan, " adalah sebesar: ")
	arr[bulan-1].total = kwh(*arr, bulan) * 30
	fmt.Println(arr[bulan-1].total, "watt")
	fmt.Print("Total penggunaan kwh listrik pada bulan ", bulan, " adalah sebesar: ")
	arr[bulan-1].kwh = arr[bulan-1].total / 1000
	fmt.Println(arr[bulan-1].kwh, "kwh")
	fmt.Print("Dengan biaya sebesar: ")
	arr[bulan-1].biaya = arr[bulan-1].kwh * 1500
	fmt.Println(big.NewInt(int64(arr[bulan-1].biaya)), "Rupiah")
	*n++
}

func kwh(arr arrayAlatElektronik, bulan int) int {
	var total int
	for i := 0; i < arr[bulan-1].jumlah; i++ {
		total += arr[bulan-1].daya[i] * int(arr[bulan-1].waktu[i])
	}
	return total
}

func printbulan(arr arrayAlatElektronik, n, bulan int) {
	var idx int
	idx = printbulanidx(arr, n, bulan)
	if idx == -1 {
		fmt.Println("Tidak valid")
	} else {
		fmt.Println("Penggunaan listrik pada bulan:", bulan)
		for i := 0; i < arr[idx].jumlah; i++ {
			fmt.Println("Barang ke-", i+1, " Jenis:", arr[idx].barang[i], " 	Daya:", arr[idx].daya[i], "Watt", " 	Rata-rata penggunaan dalam sehari:", arr[idx].waktu[i], "Jam")
		}

		fmt.Println("Total penggunaan listrik pada bulan", bulan, "adalah:", arr[idx].total, "watt")
		fmt.Println("Total penggunaan kwh listrik pada bulan", bulan, "adalah:", arr[idx].kwh, "kwh")
		fmt.Println("Dengan biaya sebesar:", arr[idx].biaya, "Rupiah")
	}
}
func printbulanidx(arr arrayAlatElektronik, n, bulan int) int {
	var ka, ki, t, idx int
	var ketemu bool
	ka = n - 1
	ki = 0
	idx = -1
	t = (ka + ki) / 2
	for ki <= ka && ketemu == false {
		if arr[t].bulan == bulan {
			ketemu = true
			idx = t
		} else if arr[t].bulan < bulan {
			ki = t + 1
			t = (ka + ki) / 2
		} else if arr[t].bulan > bulan {
			ka = t - 1
			t = (ka + ki) / 2
		}
	}
	return idx
}

func printbiaya(arr arrayAlatElektronik, n int, biaya int) {
	var idx int
	idx = printbiayaidx(arr, n, biaya)
	if idx == -1 {
		fmt.Println("Tidak valid")
	} else {
		fmt.Println("Penggunaan listrik pada bulan:", arr[idx].bulan)
		for i := 0; i < arr[idx].jumlah; i++ {
			fmt.Println("Barang ke-", i+1, " Jenis:", arr[idx].barang[i], " 	Daya:", arr[idx].daya[i], "Watt", " 	Rata-rata penggunaan dalam sehari:", arr[idx].waktu[i], "Jam")
		}

		fmt.Println("Total penggunaan listrik pada bulan", arr[idx].bulan, "adalah:", arr[idx].total, "watt")
		fmt.Println("Total penggunaan kwh listrik pada bulan", arr[idx].bulan, "adalah:", arr[idx].kwh, "kwh")
		fmt.Println("Dengan biaya sebesar:", arr[idx].biaya, "Rupiah")
	}
}

func printbiayaidx(arr arrayAlatElektronik, n int, biaya int) int {
	var idx int
	idx = -1
	for i := 0; i < n; i++ {
		if arr[i].biaya == biaya {
			idx = i
		}
	}
	return idx
}
func printsemua(arr arrayAlatElektronik, n int) {
	for i := 0; i < n; i++ {
		fmt.Println("Penggunaan pada bulan", i+1)
		for j := 0; j < arr[i].jumlah; j++ {
			fmt.Println("Barang ke-", j+1, " Jenis:", arr[i].barang[j], " 	Daya:", arr[i].daya[j], "Watt", " 	Rata-rata penggunaan dalam sehari:", arr[i].waktu[j], "Jam")
		}
		fmt.Println("Total penggunaan listrik pada bulan", i+1, "adalah:", arr[i].total, "watt")
		fmt.Println("Total penggunaan kwh listrik pada bulan", i+1, "adalah:", arr[i].kwh, "kwh")
		fmt.Println("Dengan biaya sebesar:", arr[i].biaya, "Rupiah")
	}
}

func maximum(arr arrayAlatElektronik, n int) {
	i := maxidx(arr, n)
	fmt.Print("Penggunaan listrik terbesar terdapat pada bulan: ")
	fmt.Println(i)
	fmt.Print("Sebesar: ")
	fmt.Println(arr[i-1].total, "Watt")
}

func maxidx(arr arrayAlatElektronik, n int) int {
	var max int
	var idx int
	max = arr[0].total
	idx = 0
	for i := 1; i < n; i++ {
		if arr[i].total > max {
			max = arr[i].total
			idx = i
		}
	}
	return idx + 1
}

func minimum(arr arrayAlatElektronik, n int) {
	i := minidx(arr, n)
	fmt.Print("Penggunaan listrik terkecil terdapat pada bulan: ")
	fmt.Println(i)
	fmt.Print("Sebesar: ")
	fmt.Println(arr[i-1].total, "Watt")
}

func minidx(arr arrayAlatElektronik, n int) int {
	var min int
	var idx int
	min = arr[0].total
	idx = 0
	for i := 1; i < n; i++ {
		if arr[i].total < min {
			min = arr[i].total
			idx = i
		}
	}
	return idx + 1
}

func hapus(arr *arrayAlatElektronik, bulan int, barang string) {
	var idx int
	idx = hapusidx(*arr, bulan, barang)
	if idx == -1 {
		fmt.Println("Tidak valid")
	} else {
		for i := idx; i < arr[bulan-1].jumlah; i++ {
			arr[bulan-1].barang[i] = arr[bulan-1].barang[i+1]
			arr[bulan-1].daya[i] = arr[bulan-1].daya[i+1]
			arr[bulan-1].waktu[i] = arr[bulan-1].waktu[i+1]
		}
		arr[bulan-1.].jumlah -= 1
		arr[bulan-1].total = kwh(*arr, bulan) * 30
		arr[bulan-1].kwh = arr[bulan-1].total / 1000
		arr[bulan-1].biaya = arr[bulan-1].kwh * 1500
		fmt.Println("Barang berhasil dihapus")
	}
}

func hapusidx(arr arrayAlatElektronik, bulan int, barang string) int {
	var idx int
	idx = -1
	for i := 0; i <= arr[bulan-1].jumlah-1; i++ {
		if arr[bulan-1].barang[i] == barang {
			idx = i
		}
	}
	return idx
}

func edit(arr *arrayAlatElektronik, bulan int, barang string) {
	var idx, waktu int
	var daya int
	var nama string
	idx = editidx(*arr, bulan, barang)
	if idx == -1 {
		fmt.Println("Tidak valid")
	} else {
		fmt.Print("Jenis: ")
		fmt.Scan(&nama)
		arr[bulan-1].barang[idx] = nama
		fmt.Print("Daya: ")
		fmt.Scan(&daya)
		arr[bulan-1].daya[idx] = daya
		fmt.Print("Penggunaan rata-rata dalam sehari: ")
		fmt.Scan(&waktu)
		arr[bulan-1].waktu[idx] = waktu
		arr[bulan-1].total = kwh(*arr, bulan) * 30
		arr[bulan-1].kwh = arr[bulan-1].total / 1000
		arr[bulan-1].biaya = arr[bulan-1].kwh * 1500
		fmt.Println("Barang berhasil diedit")
	}
}

func editidx(arr arrayAlatElektronik, bulan int, barang string) int {
	var idx int
	idx = -1
	for i := 0; i <= arr[bulan-1].jumlah-1; i++ {
		if arr[bulan-1].barang[i] == barang {
			idx = i
		}
	}
	return idx
}

func banding(arr arrayAlatElektronik, bulan1, bulan2 int) {
	var besar, kecil int
	var besarbulan, kecilbulan int
	besar = arr[bulan1-1].total
	besarbulan = bulan1
	kecil = arr[bulan1-1].total
	kecilbulan = bulan1
	if arr[bulan2-1].total > besar {
		besar = arr[bulan2-1].total
		besarbulan = bulan2
		fmt.Println("Penggunaan bulan", bulan1, ":", arr[bulan1-1].total, "watt")
		fmt.Println("Penggunaan bulan", bulan2, ":", arr[bulan2-1].total, "watt ")
		fmt.Println("Penggunaan listrik pada bulan", besarbulan, "dengan total daya", besar, "watt lebih besar daripada bulan", kecilbulan, "dengan total daya", kecil, "watt")
	} else if arr[bulan2-1].total < kecil {
		kecil = arr[bulan2-1].total
		kecilbulan = bulan2
		fmt.Println("Penggunaan bulan", bulan1, ":", arr[bulan1-1].total, "watt")
		fmt.Println("Penggunaan bulan", bulan2, ":", arr[bulan2-1].total, "watt ")
		fmt.Println("Penggunaan listrik pada bulan", besarbulan, "dengan total daya", besar, "watt lebih besar daripada bulan", kecilbulan, "dengan total daya", kecil, "watt")
	} else if arr[bulan2-1].total == besar && arr[bulan2-1].total == kecil {
		fmt.Println("Pengunaan listrik pada bulan", bulan1, "dengan", bulan2, "sama besar")
	}
}

func dayaterurut(arr arrayAlatElektronik, n int) {
	var min int
	for i := 0; i < n; i++ {
		min = i
		for j := i + 1; j < n; j++ {
			if arr[min].total > arr[j].total {
				min = j
			}
		}
		temp := arr[min]
		arr[min] = arr[i]
		arr[i] = temp
	}
	fmt.Println("Penggunaan listrik dari yang terkecil hingga terbesar adalah:")
	fmt.Println()
	for i := 0; i < n; i++ {
		fmt.Println("Bulan", arr[i].bulan, "total daya:", arr[i].total)

	}
}

func biayaterurut(arr arrayAlatElektronik, n int) {
	for i := 0; i < n; i++ {
		v := arr[i]
		j := i - 1
		if i >= 1 {
			for j >= 0 && arr[j].biaya > v.biaya {
				arr[j+1] = arr[j]
				j--
			}
			arr[j+1] = v
		}
	}
	fmt.Println("Biaya listrik dari yang terkecil hingga terbesar adalah:")
	fmt.Println()
	for i := 0; i < n; i++ {
		fmt.Println("Bulan", arr[i].bulan, "total biaya:", arr[i].biaya)
	}
}
