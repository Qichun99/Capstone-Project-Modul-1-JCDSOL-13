# Capstone-Project-Modul-1-JCDSOL-13
Capstone Project Modul 1 Program Data scientist kelas online

#CAPTSONE PROJECT MODULE 1 DATA SCIENCE 'Data Karyawan Perusahaan'

# DATA KARYAWAN PERUSAHAAN 
data_karyawan =[{
        'ID' : 'PP011',
        'Nama' : 'Dharmawan',
        'Jabatan' : 'Staff Manager',
        'Divisi' : 'Marketing',
    },
    {
        'ID' : 'PP007',
        'Nama' : 'Hamami',
        'Jabatan' : 'Lead Programmer',
        'Divisi' : 'Software Development',
    },
    {
        'ID' : 'PP008',
        'Nama' : 'Faris',
        'Jabatan' : 'HRD',
        'Divisi' : 'Personalia',
    }
]

#Read
def read():
    while True:
        print('''
    Data Karyawan Perusahaan 
    1. Data Seluruh Karyawan
    2. Data Karyawan
    3. Menu Utama
            ''')
        
        input_read = int(input('Masukan Menu Yang Ingin Anda Tuju :  '))

        if input_read == 1:
            print('Data Karyawan\n')
            print('ID:\t Nama:\t Jabatan:\t Divisi:\n')
            for i, j in enumerate(data_karyawan):
                print ('{}\t{}\t{}\t{}'.format(j['ID'], j['Nama'], j['Jabatan'], j['Divisi']))
        elif input_read == 2:
            read2 = (input('Masukkan "ID" Karyawan : ')).upper() 
            print(f'"ID" Karyawan : {read2}')

            for i, j in enumerate(data_karyawan):
                if read2 == j['ID']: 
                    print('ID\t Nama\t Jabatan\t Divisi\n')
                    print('{}\t {}\t {}\t {}\n'.format(j['ID'], j['Nama'], j['Jabatan'], j['Divisi']))
                    break
                elif read2 != j['ID'] and (i == len(data_karyawan) - 1): 
                    print('Karyawan Tidak Ada')
                    break
        elif input_read == 3:
            break
        else:
            print('Menu Tidak Tersedia')

#Create
def create():
    while True:
        print('''
           Penambahan Karyawan Baru 
           1. Tambah Karyawan Baru
           2. Kembali ke Menu Utama
                ''')
        input_create = int(input('Masukkan Menu Yang Ingin Anda Tuju :  ')) 

        if input_create == 1:
            input_create2 = (input('Masukkan "ID" Karyawan :  ')).capitalize() 
            for i, j in enumerate(data_karyawan):
                if input_create2 == j['ID']: 
                    print('"ID" Sudah Terdaftar')
                    break
                elif input_create2 != j['ID'] and (i == len(data_karyawan) - 1): 
                    nama_karyawan = str(input('Nama Karyawan: '))
                    jabatan_karyawan = input('Jabatan Karyawan: ')
                    divisi_karyawan = input('Divisi Karyawan: ')
                    simpan = input('Tambah Data Karyawan?(Y/N): ').upper()

                    if simpan == 'Y':
                        print('Data Karyawan Ditambahkan')
                        data_karyawan.append({
                            'ID': input_create2, 
                            'Nama': nama_karyawan,
                            'Jabatan': jabatan_karyawan,
                            'Divisi': divisi_karyawan,
                        })
                    elif simpan == 'N':
                        print('Data Tidak Disimpan')
                    else:
                        print('Masukkan Pilihan Yang Sesuai (Y/N)')
                        break
        elif input_create == 2:
            break
        else: 
            print ('Masukkan Opsi Yang Ada')

#Update
def update():
    while True: 
        print('''
    Update Data Karyawan
    1. Update Data
    2. Kembali Ke Menu Utama
                ''')
        input_update = int(input('Pilih Menu Yang Ingin Anda Tuju: '))
            
        if input_update == 1:
            input_update2 = (input('Masukkan "ID" Pegawai: ')).capitalize()

            for i, j in enumerate(data_karyawan):
                if input_update2 == j['ID']:
                    print('ID\t Nama\t Jabatan\t Divisi\n') 
                    print('{}\t {}\t {}\t {}\n'.format(j['ID'], j['Nama'], j['Jabatan'], j['Divisi']))

                    input_update3 = input('Pilih (Y/N) Untuk Melanjutkan: ').capitalize()
                    if input_update3 == 'Y':
                        update_kolom = input('Masukkan Kolom Yang Ingin Ditambahkan: ').capitalize()
                        for key in j.keys():
                            if update_kolom == key:
                                input_update4 = input(f'Masukkan {update_kolom}: ').capitalize()
                                input_update5 = input('Update Data Karyawan? (Y/N): ').upper()
                                if input_update5 == 'Y':
                                    j[update_kolom] = input_update4
                                    print('Data Di Update')
                                elif input_update5 == 'N':
                                    print('Data Gagal Ditambahkan')
                                else:
                                    print('Pilih Opsi (Y/N)!')
                                break
                    else:
                        break
                    break
                         
                elif input_update2 != j['ID'] and (i == len(data_karyawan)-1):
                    print('Data Tidak Ada')
                    break
        elif input_update == 2:
            break
        else:
            print('Pilih Opsi (1/2)!')

#Delete
def delete():
    while True:
        print('''
                Hapus Data Karyawan
                1. Hapus Data
                2. Menu Utama''')
        input_delete = int(input('Pilih Menu Yang Anda Ingin Tuju: '))

        if input_delete == 1:
            input_delete2 = (input('Masukkan "ID" Karyawan Yang Ingin Anda Hapus')).capitalize()

            for i, j in enumerate(data_karyawan):
                if input_delete2 == j['ID']:
                    print('ID\t Nama\t Jabatan\t Divisi\n') 
                    print('{}\t {}\t {}\t {}\n'.format(j['ID'], j['Nama'], j['Jabatan'], j['Divisi']))
                    delete_data = input('Hapus Data Karyawan?:  (Y/N)').upper()
                    if delete_data == 'Y':
                        del data_karyawan[i]
                        print('Data Karyawan Berhasil Dihapus')
                    elif delete_data == 'N':
                        print('Tidak Karyawan Gagal Dihapus')
                    else: 
                        print('Pilih Sesuai Opsi (Y/N)')
                        break
                elif input_delete2 != j['ID'] and (i == len(data_karyawan)-1):
                    print('Data Tidak Ditemukan')
                    break
        elif input_delete == 2:
            break
        else:
            print('Pilih Opsi 1/2')

#Menu Utama
def menu():
    while True : 
        menu_utama = input('''
Data Karyawan Perusahaan

1. Data karyawan perusahaan
2. Tambah karyawan
3. Hapus data karyawan
4. Update data karyawan
5. Keluar
                               
Masukan Menu Yang Ingin Anda Tuju : ''')
        if menu_utama == '1':
            read()
        elif menu_utama == '2':
            create()
        elif menu_utama == '3':
            delete()
        elif menu_utama == '4':
            update()
        elif menu_utama == '5':
            break
        else:
            print ('Menu Yang Dituju Tidak Tersedia')

menu()
