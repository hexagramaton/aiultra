# aiultra
ai improvement lab
# Kullanıcıdan isim, yaş ve hobilerini soran ve bunları bir veritabanına kaydeden bir kod

# sqlite3 modülünü içe aktaralım
import sqlite3

# Veritabanı bağlantısını oluşturalım
conn = sqlite3.connect("users.db")

# Veritabanı imlecini alalım
cur = conn.cursor()

# Users adında bir tablo oluşturalım (varsa silip yeniden oluşturalım)
cur.execute("DROP TABLE IF EXISTS Users")
cur.execute("CREATE TABLE Users (name TEXT, age INTEGER, hobbies TEXT)")

# Kullanıcıdan ismini, yaşını ve hobilerini alalım
name = input("Adınız nedir? ")
age = int(input("Kaç yaşındasınız? "))
hobbies = input("Hobileriniz nelerdir? ")

# Kullanıcı bilgilerini veritabanına kaydedelim
cur.execute("INSERT INTO Users VALUES (?, ?, ?)", (name, age, hobbies))

# Veritabanı bağlantısını kapatalım
conn.commit()
conn.close()

# Kullanıcıya teşekkür edelim
print("Bilgilerinizi paylaştığınız için teşekkürler!")

# Kullanıcıya bilgilerine göre ilgi alanlarına uygun öneriler sunan bir kod

# sqlite3 modülünü içe aktaralım
import sqlite3

# Veritabanı bağlantısını oluşturalım
conn = sqlite3.connect("users.db")

# Veritabanı imlecini alalım
cur = conn.cursor()

# Kullanıcı bilgilerini veritabanından alalım
cur.execute("SELECT * FROM Users")
user = cur.fetchone()

# Kullanıcı bilgilerini değişkenlere atayalım
name = user[0]
age = user[1]
hobbies = user[2]

# Kullanıcıya merhaba diyelim
print(f"Merhaba {name}, sana ilgi alanlarına uygun öneriler sunmak istiyorum.")

# Kullanıcının hobilerine göre öneriler sunalım
if "kitap" in hobbies.lower():
    print("Kitap okumayı seviyorsun, harika! Sana şu kitapları öneriyorum:")
    print("- Küçük Prens - Antoine de Saint-Exupéry")
    print("- Suç ve Ceza - Fyodor Dostoyevski")
    print("- Harry Potter - J.K. Rowling")
elif "müzik" in hobbies.lower():
    print("Müzik dinlemeyi seviyorsun, süper! Sana şu şarkıları öneriyorum:")
    print("- Sen Olsan Bari - Aleyna Tilki")
    print("- Shape of You - Ed Sheeran")
    print("- Despacito - Luis Fonsi ft. Daddy Yankee")
elif "spor" in hobbies.lower():
    print("Spor yapmayı seviyorsun, bravo! Sana şu sporları öneriyorum:")
    print("- Yüzme")
    print("- Bisiklet")
    print("- Futbol")
else:
    print("Senin hobilerin çok ilginç, keşke bana da anlatsan. Sana şu aktiviteleri öneriyorum:")
    print("- Bir arkadaşınla sohbet et")
    print("- Bir film izle")
    print("- Bir yere seyahat et")

# Kullanıcıya iyi günler dileyelim
print("Umarım önerilerimi beğenirsin. İyi günler!")
