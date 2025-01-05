
# **Input Program**
```python
class Student:
    """Class untuk menyimpan data mahasiswa."""
    def __init__(self, name, age, major):
        self.name = name
        self.age = age
        self.major = major


class StudentView:
    """Class untuk menampilkan data mahasiswa."""
    @staticmethod
    def display_students(students):
        print("\nDaftar Mahasiswa:")
        print(f"{'No':<5} {'Nama':<20} {'Usia':10} {'Jurusan':<15}")
        print("-" * 50)
        for index, student in enumerate(students, start=1):
            print(f"{index:<5} {student.name:<20} {student.age:<10} {student.major:<15}")


class StudentProcess:
    """Class untuk memproses input dan validasi data mahasiswa."""
    def __init__(self):
        self.students = []

    def add_student(self, name, age, major):
        if not name or not major:
            raise ValueError("Nama dan jurusan tidak boleh kosong.")
        if age <= 0:
            raise ValueError("Usia harus lebih besar dari 0.")
        
        student = Student(name, age, major)
        self.students.append(student)

    def get_students(self):
        return self.students


def main():
    process = StudentProcess()

    while True:
        try:
            name = input("Masukkan nama mahasiswa (atau ketik 'exit' untuk keluar): ")
            if name.lower() == 'exit':
                break
            
            age = int(input("Masukkan usia mahasiswa: "))
            major = input("Masukkan jurusan mahasiswa: ")

            process.add_student(name, age, major)

        except ValueError as e:
            print(f"Error: {e}")

    # Menampilkan data mahasiswa
    view = StudentView()
    view.display_students(process.get_students())


if __name__ == "__main__":
    main()
```
# **Penjelasan Program**
 1. Class `Student`: Kelas ini menyimpan informasi tentang mahasiswa, termasuk nama, usia, dan jurusan.
 2. Class `StudentView`: Kelas ini memiliki metode statis `display_students` yang menampilkan daftar mahasiswa dalam format tabel.
 3. Class `StudentProcess`: Kelas ini mengelola logika untuk menambahkan mahasiswa dan menyimpan data mahasiswa. Metode `add_student` melakukan validasi input dan menambahkan mahasiswa ke dalam daftar.
 4. Fungsi `main`: Fungsi utama yang meminta input dari pengguna dan menangani eksepsi jika terjadi kesalahan. Setelah pengguna selesai memasukkan data, program akan menampilkan daftar mahasiswa.

# **Output**
```python
Masukkan nama mahasiswa (atau ketik 'exit' untuk keluar): aziz
Masukkan usia mahasiswa: 20
Masukkan jurusan mahasiswa: informatika 
Masukkan nama mahasiswa (atau ketik 'exit' untuk keluar): exit

Daftar Mahasiswa:
No    Nama                 Usia       Jurusan        
--------------------------------------------------
1     aziz                 20         informatika
```
    





