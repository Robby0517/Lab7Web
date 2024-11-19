# Lab7Web Penjelasan,codingan dan SS


Nama : Robi Jaelani
NIM : 312310517
Laporan Praktikum 7 php dasar

1.	Penerapan php dasar pertama.
Ini hanya menampilkan text:
  <!DOCTYPE html>
          <html lang="en">
          <head>
              <meta charset="UTF-8">
              <title>PHP Dasar</title>
          </head>
          <body>
              <h1>Belajar PHP Dasar</h1>
              <?php 
              echo "Hello World"; 
              ?>
       
![image](https://github.com/user-attachments/assets/4c8f5112-574c-4e96-b45b-568c99dc5f50)


2.	Penerrapan php dasar ke2.
Menampilkan text hello world dan data pengguna:

<h2>Menggunakan Variable</h2>
        
        <?php 
        $nim = "312310517"; 
        $nama = 'Robi Jaelani'; 
        echo "NIM : " . $nim . "<br>"; 
        echo "Nama : $nama"; 
        ?>
    </body>
    </html>
 
![image](https://github.com/user-attachments/assets/793d5735-65fe-4daf-b45f-a1a87fa8cf35)


3.	Penerapan Predefine Variable $_GET.
Menampilkan  ucapan selamat datang pada pengguna:
   <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>PHP Dasar</title>
            </head>
            <body>
                <h1>Predefine Variable</h1>
                <?php 
                echo 'Selamat Datang ' . $_GET['nama']; 
                ?>
            </body>
            </html>

 
![image](https://github.com/user-attachments/assets/408085f4-3f42-45d0-badb-db6f5b9b01c5)




4.	Penerapan Membuat Form Input.
Mengetik nama dan menghasilkan ucapan selamat datang sesuai dengan nama yang dimasukan:

   <!DOCTYPE html> 
    <html lang="en"> 
    <head> 
        <meta charset="UTF-8"> 
         <title>PHP Dasar</title> 
        </head> 
        <body> 
    <h2>Form Input</h2> 
    <form method="post"> 
        <label>Nama: </label> 
        <input type="text" name="nama"> 
        <input type="submit" value="Kirim"> 
    </form> 
    <?php 
    echo 'Selamat Datang ' . $_POST['nama']; 
    ?> 
    </body> 
    </html>


![image](https://github.com/user-attachments/assets/84f19dd0-a4ad-45d0-9e75-0be9552306d3)
 

5.	Penerapan From input gajih.
Memasukan nama dan gajih sehingga menampilkan gaji sebelum pajak dan sesudah pajak:


![image](https://github.com/user-attachments/assets/2d0ce7a7-ebd3-4558-b5c3-94dc2006ced2)
 

6.	Penerapan tugas yang diberikan, form input yang menampilkan  nama, tanggal lahir dan pekerjaan. Kemudian tampilkan outputnya dengan menghitung  umur berdasarkan inputan tanggal lahir. Dan pilihan pekerjaan dengan gaji yang  berbeda-beda sesuai pilihan pekerjaan. 
<!DOCTYPE html> 
    <html lang="en"> 
    <head> 
        <meta charset="UTF-8"> 
        <title>PHP Dasar</title> 
    </head> 
    <body> 
        <h2>Form Input</h2> 
        <form method="post"> 
            <label>Nama: </label> 
            <input type="text" name="nama" required> 
            <br><br>
            <label>Tanggal Lahir: </label> 
            <input type="date" name="tanggal_lahir" required> 
            <br><br>
            <label>Pekerjaan: </label> 
            <select name="pekerjaan" required>
                <option value="Programmer">Programmer</option>
                <option value="Designer">Designer</option>
                <option value="Manager">Manager</option>
            </select>
            <br><br>
            <input type="submit" value="Kirim"> 
        </form> 
    
       <?php 
        // Proses input
        if (isset($_POST['nama']) && isset($_POST['tanggal_lahir']) && isset($_POST['pekerjaan'])) {
            $nama = htmlspecialchars($_POST['nama']); 
            $tanggal_lahir = $_POST['tanggal_lahir']; 
            $pekerjaan = $_POST['pekerjaan'];
    
            // Hitung umur
            $tanggal_lahir_datetime = new DateTime($tanggal_lahir);
            $today = new DateTime();
            $umur = $today->diff($tanggal_lahir_datetime)->y;
    
            // Gaji berdasarkan pekerjaan
            $gaji = 0;
            switch ($pekerjaan) {
                case "Programmer":
                    $gaji = 8000000;
                    break;
                case "Designer":
                    $gaji = 7000000;
                    break;
                case "Manager":
                    $gaji = 10000000;
                    break;
            }
    
            // Tampilkan hasil
            echo "<h3>Hasil:</h3>";
            echo "<p>Nama: $nama</p>";
            echo "<p>Tanggal Lahir: $tanggal_lahir</p>";
            echo "<p>Umur: $umur tahun</p>";
            echo "<p>Pekerjaan: $pekerjaan</p>";
            echo "<p>Gaji: Rp. " . number_format($gaji, 0, ',', '.') . "</p>";
        }
        ?>
    
       <h2>Hari Saat Ini</h2>
        <?php 
        // Nama hari menggunakan if-else
        $nama_hari = date("l"); 
        echo "<p>Dengan if-else: ";
        if ($nama_hari == "Sunday") { 
            echo "Minggu"; 
        } elseif ($nama_hari == "Monday") { 
            echo "Senin"; 
        } elseif ($nama_hari == "Tuesday") { 
            echo "Selasa"; 
        } else { 
            echo "Hari lainnya"; 
        }
        echo "</p>";
    
      // Nama hari menggunakan switch
        echo "<p>Dengan switch: ";
        switch ($nama_hari) { 
            case "Sunday": 
                echo "Minggu"; 
                break; 
            case "Monday": 
                echo "Senin"; 
                break;
            case "Tuesday": 
                echo "Selasa"; 
                break; 
            default: 
                echo "Hari lainnya"; 
        }
        echo "</p>";
        ?>
    
       <h2>Perulangan</h2>
        <?php 
        // Perulangan for
        echo "Perulangan 1 sampai 10 dengan for:<br>";
        for ($i = 1; $i <= 10; $i++) { 
            echo "Perulangan ke: " . $i . '<br>'; 
        }
    
       // Perulangan menurun
        echo "Perulangan menurun dari 10 ke 1 dengan for:<br>";
        for ($i = 10; $i >= 1; $i--) { 
            echo "Perulangan ke: " . $i . '<br>'; 
        }
    
      // Perulangan while
        echo "Perulangan 1 sampai 10 dengan while:<br>";
        $i = 1; 
        while ($i <= 10) { 
            echo "Perulangan ke: " . $i . '<br>'; 
            $i++; 
        }
    
      // Perulangan do-while
        echo "Perulangan 1 sampai 10 dengan do-while:<br>";
        $i = 1; 
        do { 
            echo "Perulangan ke: " . $i . '<br>'; 
            $i++; 
        } while ($i <= 10); 
        ?>
    </body> 
    </html>
     
![image](https://github.com/user-attachments/assets/e6f4b3f4-3c66-4af9-a7c5-f1be47118a8b)

![image](https://github.com/user-attachments/assets/b2a92bd3-d19a-4c33-947c-1500382e2525)


 
