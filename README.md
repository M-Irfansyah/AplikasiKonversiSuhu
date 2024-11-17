# AplikasiKonversiSuhu
 Tugas 2- M.Irfansyah 2210010176
# 1. Deskripsi Program
Program Konversi Suhu ini adalah aplikasi sederhana berbasis Java yang memungkinkan pengguna untuk memasukkan nilai suhu dalam skala Celcius dan mengonversinya ke skala suhu lain, yaitu Fahrenheit, Reamur, atau Kelvin. Program ini dibuat menggunakan JFrame sebagai antarmuka pengguna dan dijalankan melalui NetBeans IDE 8.2.

• Pengguna memasukkan nilai suhu dan memilih jenis konversi

• Hasil konversi ditampilkan setelah tombol ditekan.

# 2. Komponen GUI ke JFrame
- JPanel: Sebagai panel utama untuk menampung komponen lainnya.
- JLabel: Untuk judul, label input suhu, dan label hasil konversi.
- JTextField: Untuk pengguna memasukkan nilai suhu.
- JComboBox: Untuk memilih skala suhu awal.
- JRadioButton: Untuk memilih skala suhu tujuan (misalnya Fahrenheit, Reamur, Kelvin).
- JButton: Untuk memproses konversi suhu.

Metode Konversi: 

• Tombol-tombol radio untuk memilih skala suhu awal.
Pilihan mode konversi suhu:
- Celsius ke skala lain
- Fahrenheit ke skala lain
- Kelvin ke skala lain
- Reamur ke skala lain
  
• Kotak kombo untuk memilih skala suhu tujuan.
Program ini memiliki metode konversi dari masing-masing skala suhu ke skala lainnya:
* celsiusToFahrenheit, celsiusToKelvin, celsiusToReamur
* fahrenheitToCelsius, fahrenheitToKelvin, fahrenheitToReamur
* kelvinToCelsius, kelvinToFahrenheit, kelvinToReamur
* reamurToCelsius, reamurToFahrenheit, reamurToKelvin

• Hasil konversi ditampilkan setelah tombol ditekan. Input suhu yang validasi otomatis untuk hanya menerima angka dan desimal.

# 3. Logika Program:
Rumus konversi, validasi input
   
# 4. Events

• ActionListener untuk tombol Konversi
```
 private void btnKonversiActionPerformed(java.awt.event.ActionEvent evt) {                                            
    try {    
            double inputsuhu = Double.parseDouble(inputSuhu.getText());
            String hasilKonversi = (String) jenisKonversi.getSelectedItem();
            double hasil = 0.0;

        // Periksa arah konversi berdasarkan pilihan JRadioButton
        if (Celsius.isSelected()) {
            // Konversi dari Celsius ke skala yang dipilih
            switch (hasilKonversi) {
                case "Celsius ke Fahrenheit":
                    hasil = celsiusToFahrenheit(inputsuhu);
                    break;
                case "Celsius ke Kelvin":
                    hasil = celsiusToKelvin(inputsuhu);
                    break;
                case "Celsius ke Reamur":
                    hasil = celsiusToReamur(inputsuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                    
            }
        } else if (Fahrenheit.isSelected()) {
            // Konversi dari Fahrenheit ke skala yang dipilih
            switch (hasilKonversi) {
                case "Fahrenheit ke Celsius":
                    hasil = fahrenheitToCelsius(inputsuhu);
                    break;
                case "Fahrenheit ke Kelvin":
                    hasil = fahrenheitToKelvin(inputsuhu);
                    break;
                case "Fahrenheit ke Reamur":
                    hasil = fahrenheitToReamur(inputsuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;    
            }
        
        } else if (Reamur.isSelected()) {
            switch (hasilKonversi) {
                case "Reamur ke Celsius":
                    hasil = reamurToCelsius(inputsuhu);
                    break;
                case "Reamur ke Fahrenheit":
                    hasil = reamurToFahrenheit(inputsuhu);
                    break;
                case "Reamur ke Kelvin":
                    hasil = reamurToKelvin(inputsuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                }
            } else if (Kelvin.isSelected()) {
            switch (hasilKonversi) {
                case "Kelvin ke Celsius":
                    hasil = kelvinToCelsius(inputsuhu);
                    break;
                case "Kelvin ke Fahrenheit":
                    hasil = kelvinToFahrenheit(inputsuhu);
                    break;
                case "Kelvin ke Reamur":
                    hasil = kelvinToReamur(inputsuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
            }
            }
        

         labelHasil.setText("" + hasil);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan angka yang valid!");
        }                                               
    } 
```   
• Tombol Konversi diklik akan menampilkan hasil konversi dari
```
// Dari Celsius ke skala lain
private double celsiusToFahrenheit(double celsius) {
    return (celsius * 9/5) + 32;
}

private double celsiusToReamur(double celsius) {
    return celsius * 4/5;
}

private double celsiusToKelvin(double celsius) {
    return celsius + 273.15;
}
// Dari Fahrenheit ke skala lain
private double fahrenheitToCelsius(double fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

private double fahrenheitToReamur(double fahrenheit) {
    return (fahrenheit - 32) * 4/9;
}

private double fahrenheitToKelvin(double fahrenheit) {
    return (fahrenheit - 32) * 5/9 + 273.15;
} 
~~~

5. Variasi:
• Tambahkan skala suhu lain seperti Reamur dan Kelvin
~~~
// Dari Kelvin
private double kelvinToCelsius(double kelvin) {
    return kelvin - 273.15;
}

private double kelvinToFahrenheit(double kelvin) {
    return (kelvin - 273.15) * 9/5 + 32;
}

private double kelvinToReamur(double kelvin) {
    return (kelvin - 273.15) * 4/5;
}
    
// Dari Reamur
private double reamurToCelsius(double reamur) {
    return reamur * 5/4;
}

private double reamurToFahrenheit(double reamur) {
    return reamur * 9/4 + 32;
}

private double reamurToKelvin(double reamur) {
    return reamur * 5/4 + 273.15;
}

```
• Tambahkan ItemListener pada JRadioButton untuk memilih arah konversi
```
 private void CelsiusItemStateChanged(java.awt.event.ItemEvent evt) {                                         
    if (evt.getStateChange() == ItemEvent.SELECTED) {
            jenisKonversi.removeAllItems();
            jenisKonversi.addItem("Celsius ke Fahrenheit");
            jenisKonversi.addItem("Celsius ke Kelvin");
            jenisKonversi.addItem("Celsius ke Reamur");
        }    
    }                                        

    private void FahrenheitItemStateChanged(java.awt.event.ItemEvent evt) {                                            
    if (evt.getStateChange() == ItemEvent.SELECTED) {
            jenisKonversi.removeAllItems();
            jenisKonversi.addItem("Fahrenheit ke Celsius");
            jenisKonversi.addItem("Fahrenheit ke Kelvin");
            jenisKonversi.addItem("Fahrenheit ke Reamur");        
    }                                           
    }
    private void ReamurItemStateChanged(java.awt.event.ItemEvent evt) {                                        
    if (evt.getStateChange() == ItemEvent.SELECTED) {
            jenisKonversi.removeAllItems();
            jenisKonversi.addItem("Reamur ke Celsius");
            jenisKonversi.addItem("Reamur ke Fahrenheit");
            jenisKonversi.addItem("Reamur ke Kelvin");
        }
    }                                       

    private void KelvinItemStateChanged(java.awt.event.ItemEvent evt) {                                        
    if (evt.getStateChange() == ItemEvent.SELECTED) {
            jenisKonversi.removeAllItems();
            jenisKonversi.addItem("Kelvin ke Celsius");
            jenisKonversi.addItem("Kelvin ke Fahrenheit");
            jenisKonversi.addItem("Kelvin ke Reamur");
        }
    } 

 ```
• Implementasikan konversi otomatis saat nilai input berubah
```
public KonversiSuhuFrame() {
        initComponents();
        setupDocumentListener();
    }
    private void setupDocumentListener(){    
    inputSuhu.getDocument().addDocumentListener(new javax.swing.event.DocumentListener() {
    @Override
    public void insertUpdate(javax.swing.event.DocumentEvent e) {
        btnKonversiActionPerformed();
    }
    
    @Override
    public void removeUpdate(javax.swing.event.DocumentEvent e) {
        btnKonversiActionPerformed();
    }
    
    @Override
    public void changedUpdate(javax.swing.event.DocumentEvent e) {
        btnKonversiActionPerformed();
    }
    private void btnKonversiActionPerformed(){
    }
    });
```

# Hasil Gambar Project Ketika di Run
![Konversi suhu2](https://github.com/user-attachments/assets/138f586d-8450-4a5e-a700-d9576c8effb9)
![konversi suhu 1](https://github.com/user-attachments/assets/52b65220-6ea2-4053-bd63-b4e7f0edd846)

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    10    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    40    |
|     | TOTAL        | 100 |

## Pembuat

Nama  : M.Irfansyah

NPM   : 2210010176
