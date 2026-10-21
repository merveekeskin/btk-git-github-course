# 📚 Versiyon Kontrolü: Git ve GitHub Eğitimi Ders Notları
**Eğitmen:** Atıl Samancıoğlu  

---

## 💻 1. Temel Terminal ve Sistem Komutları

Yazılım geliştirme sürecinde terminal (komut satırı) verimli çalışmak için temel araçtır.

* **`cmd`:** Windows işletim sisteminde Komut İstemi (Command Prompt) ekranını açar.
* **`Windows + R`:** Çalıştır (Run) kutusunu açarak hızlıca program veya komut tetiklemeyi sağlar.
* **`ipconfig`:** Bilgisayarın yerel ağdaki IP adreslerini ve ağ yapılandırma detaylarını listeler.
* **`pwd` (Print Working Directory):** Terminalde o an aktif olarak bulunulan klasörün tam dosya yolunu ekrana yazdırır.
* **`ls`:** Aktif klasörün içindeki dosya ve alt klasör isimlerini listeler.
* **`ls -la`:** Aktif klasördeki tüm dosyaları; gizli dosyalar (başında nokta olan `.git` gibi) ve detaylı izin bilgileri de dahil olmak üzere listeler.
* **`cd <klasor_adi>` (Change Directory):** Belirtilen alt klasörün içerisine giriş yapmayı sağlar.
* **`cd ..`:** Dosya dizininde bir üst klasöre (geriye) geçiş yapar.
* **`Tab Tuşu`:** Terminalde yazılan komutların veya dosya isimlerinin otomatik olarak tamamlanmasını sağlar.
* **`mkdir <klasor_adi>` (Make Directory):** Aktif dizinde sıfırdan yeni bir klasör oluşturur.
* **`touch <dosya_adi>.<uzanti>`:** Belirtilen isim ve uzantıda boş bir dosya oluşturur.
* **`rm <dosya_adi>.<uzanti>` (Remove):** Belirtilen dosyayı kalıcı olarak siler.
* **`rm -rf <klasor_adi>`:** Belirtilen klasörü ve içerisindeki tüm alt dosyaları zorlayarak ve kalıcı olarak siler.
* **`clear`:** Terminal ekranındaki eski komut geçmişini temizleyerek temiz bir satır açar.

---

## 🛠️ 2. Git İlk Kurulum ve Kimlik Ayarları

Git kurulduktan sonra, yapılan kayıtların kimin tarafından yapıldığının tarihe işlenmesi için global kimlik ayarları yalnızca bir kez tanımlanır.

* **`git --version`:** Bilgisayarda kurulu olan Git yazılımının güncel sürümünü gösterir.
* **`git` / `git --help`:** Kullanılabilecek temel Git komutlarını ve yardım dokümantasyonunu listeler.
* **`git config --global user.name "<ad_soyad>"`:** Yapılacak tüm commit'lere yazar adı olarak basılacak küresel kullanıcı adını tanımlar.
* **`git config user.name`:** Sistemde aktif olarak tanımlı olan kullanıcı adını ekranda doğrulamak için kullanılır.
* **`git config --global user.email "<e_posta>"`:** Yapılacak tüm commit'lere yazar imzası olarak basılacak küresel e-posta adresini tanımlar.
* **`git config user.email`:** Sistemde aktif olarak tanımlı olan e-posta adresini ekranda doğrulamak için kullanılır.

---

## 🎯 3. Git Temel Kavramları ve İş Akışı

Git mimarisi üç temel alandan oluşur: Çalışma Dizini (Working Directory), Sahne (Staging Area) ve Yerel Depo (Local Repository).

* **Local Repository (Yerel Depo):** Git'in projenin tüm geçmişini, branch'lerini, commit'lerini ve versiyon kayıtlarını bilgisayarınızda sakladığı gizli veritabanıdır (`.git` klasörü).
* **Index / Staging Area (Sahne):** Yapılan değişiklikler ile bu değişiklikleri kalıcı olarak kaydeden commit işlemi arasındaki bekleme odasıdır.
* **Commit:** Projede yapılan değişikliklerin o anki durumunun (Snapshot) yerel veritabanına kalıcı olarak mühürlenmesi ve geçmişe bir iz bırakılması işlemidir.
* **`git init` (Initialize):** Sıradan bir klasörü, Git'in takip mekanizmasına dahil ederek yerel bir Git deposuna dönüştürür. Herhangi bir yerde `git init` çalıştırmadan önce mutlaka `git status` ile durum kontrol edilmelidir.
* **`git status`:** Projenin o anki Git durumunu özetler; hangi dosyaların değiştirildiğini, hangilerinin sahnede onay beklediğini gösterir.
* **`git add <dosya_adi>`:** Belirtilen dosyadaki değişiklikleri sahne alanına (Staging Area) taşır.
* **`git add .`:** Çalışma dizininde yapılan tüm yeni eklemeleri, silmeleri ve değişiklikleri tek bir hamlede sahne alanına aktarır.
* **`git commit -m "<commit_mesaji>"`:** Sahne alanındaki tüm dosyaları mühürleyerek kalıcı bir geçmiş noktası oluşturur. Mesajların dünya standartlarında kısa, öz ve genellikle İngilizce yazılması tercih edilir.
* **`git log`:** Projede atılan tüm commit'lerini kronolojik olarak listeler. Log listesi uzadığında terminal satırının altında `END` uyarısı çıkar. Bu ekrandan çıkıp normal terminal satırına dönmek için klavyeden **`q` (quit)** tuşuna basılması gerekir.

---

## 🙈 4. Dosya Gizleme ve Yapılandırma (`.gitignore`)

Projelerde herkesle paylaşılmaması gereken gizli veriler, şifreler veya log klasörleri asla sahneye alınmamalı ve GitHub'a gönderilmemelidir.

* **`.gitignore`:** Git'in takip etmesini, kaydetmesini veya uzak sunucuya göndermesini istemediğiniz dosya ve klasörlerin isimlerini belirttiğiniz özel bir yapılandırma dosyasıdır.
* *Açık Kaynak Şablonları:* Her yazılım dilinin kendine has uzak durulması gereken gereksiz dosya listeleri vardır. Dünya standartlarında bir proje başlatırken [GitHub Gitignore Deposu](https://github.com) üzerinden hazır dil şablonları projeye dahil edilebilir.

---

## 🌿 5. Branş (Branch) Yönetimi ve Birleştirme (Merge)

Branşlar, ana kod hattını (varsayılan olarak `main` veya `master`) riske atmadan bağımsız olarak özellik geliştirmek, hata çözmek veya denemeler yapmak için açılan güvenli çalışma alanlarıdır.

* **Head:** Git mimarisinde şu an tam olarak hangi konumda, hangi branşta veya hangi commit'te durduğumuzu gösteren aktif işaretçidir.
* **`git branch`:** Mevcut depoda yer alan tüm branşları listeler ve o an aktif olan branşı işaret ederek gösterir.
* **`git branch <yeni_brans_adi>`:** Ana koldan ayrılan, bağımsız yeni bir çalışma dalı oluşturur.
* **`git switch <brans_adi>`:** Belirtilen branşın içerisine geçiş yaparak `HEAD` işaretçisini oraya taşır.
* **`git merge <brans_adi>`:** Farklı dallarda yaptığınız değişiklikleri tek bir dalda birleştirmeye yarayan komuttur. Hangi dalın içine kod çekmek istiyorsanız, önce o dala geçiş yapmalısınız.
* **Fast-Forwarding:** İki branş birleştirilirken, arada hiçbir çakışan geçmiş olmadığı için hedef branşın ucunun doğrudan ana branşın en önüne taşınmasıyla yapılan hızlı ve sorunsuz birleştirme şeklidir.
* **Merge Conflict (Birleştirme Çatışması):** İki farklı branşta aynı dosyanın aynı satırında değişiklik yapıldığında, Git'in hangi satırı kabul edeceğine otomatik karar veremeyip birleştirmeyi durdurması hatasıdır.

---

## 📥 6. Kaydedilmemiş Değişikliklerin Sızması ve Stash Mekanizması

Git'te branchler yalnızca commit edilmiş geçmişi takip eder. Çalışma dizini ve geçiş bölgesi ise henüz bir branche ait değildir. Bir branchte değişiklik yapıp bunu commitlemediğinizde, başka bir branche geçiş yaparsanız Git bu kaydedilmemiş değişiklikleri geçtiğiniz branche beraberinde taşır.

### Çözüm Yolları:
1. **Commit Etmek:** Değişiklikleri mevcut branşa kalıcı olarak kaydedip öyle branş değiştirmek.
2. **Değişiklikleri Geri Almak (`git restore`):** Yapılan değişikliklerden tamamen vazgeçmek.
   * **`git restore <dosya_adi>`:** Çalışma dizinindeki veya sahne alanındaki dosyaları eski/istenen durumuna geri getirmek için kullanılır.
3. **Zulaya Kaldırmak (`git stash`):** Kodları commitlemeden geçici bir hafızaya alıp çalışma alanını temizlemek.
   * **`git stash`:** Üzerinde çalışılan ama henüz commitlemediğiniz kodları kaybetmeden geçici bir kenara (zulaya) kaldırmanızı sağlar.
   * **`git stash list`:** Geçici hafızaya kaldırılmış olan tüm paketleri kronolojik bir liste halinde görüntüler.
   * **`git stash pop`:** Zulaya kaldırılan en son değişiklik paketini geri getirerek mevcut kodun üzerine uygular ve o paketi zulanın içinden kalıcı olarak siler.
   * **`git stash apply stash@{<index>}`:** Zulanın belirli bir indeksindeki paketi (Örn: `stash@{0}`) mevcut branşa uygular ancak paketi zula listesinden silmez.
   * **`git stash clear`:** Geçici hafizada birikmiş olan tüm eski paketleri tek bir hamlede kalıcı olarak temizler.

---

## 🕰️ 7. Git Geçmişinde Gezinme ve HEAD Durumları

Eski commit'lere dönmek, projenin geçmişteki kararlı bir anını incelemek için kritik bir süreçtir.

* **`git checkout <commit_ID>`:** Belirtilen commit kimlik kodunu kullanarak projenin geçmişteki o zaman dilimine geri dönmeyi ve kodları incelemeyi sağlar.
* **Detached HEAD (Ayrılmış HEAD):** `HEAD` işaretçisinin canlı ve aktif bir branş yerine doğrudan geçmişteki spesifik bir commit nesnesine bakması durumudur.
* **Reattached HEAD (Yeniden Bağlanmış HEAD):** "Detached HEAD" modundan güvenli bir şekilde çıkıp, işaretçiyi yeniden ana branş hatlarına bağlama işlemine verilen isimdir.

### Detached HEAD Durumundan Kurtulma Yolları:

* **Senaryo A (Değişiklik Yapılmadıysa):** Sadece geçmişe bakıp inceleme yaptıysanız, hiçbir ek işlem yapmadan doğrudan ana branşınıza geri dönerek HEAD'i yeniden bağlayabilirsiniz:
  ```bash
  git switch master  # veya git switch main
  ```

* **Senaryo B (Değişiklik Yapıldıysa ve Kaydedilmek İsteniyorsa):** Geçmiş commit'in üzerindeyken denemeler yaptıysanız ve bu kodları korumak istiyorsanız, sırasıyla şu adımları takip etmelisiniz:
  ```bash
  git branch <yeni_brans_adi>   # Geçmiş commit üzerinde yeni bir dal üretir
  git switch <yeni_brans_adi>   # Yeni dala geçerek HEAD işaretçisini bağlar
  git add .                     # Değişiklikleri sahneye alır
  git commit -m "Mesajiniz"     # Değişiklikleri yeni dalda kalıcı hale getirir
  ```

---

## 🕰️ 8. Gelişmiş Geçmiş Yönetimi (Reset & Revert)

Git'te hatalı yapılan işlemleri geri almak veya geçmişi düzenlemek için farklı senaryolara uygun komutlar bulunur.

* **`git reset <commit_ID>`:** Seçilen commit anından sonra atılmış olan tüm commit'leri iptal eder. Bu komutun en önemli özelliği, commit'ler silinse bile o commit'lerin içinde yazdığınız kod değişikliklerinin bilgisayarınızdan silinmemesidir (Kodlar çalışma dizininde kalır).
* **`git reset --hard <commit_ID>`:** Git mimarisindeki en keskin ve geri dönüşü olmayan komutlardan biridir. Projenin geçmişini, geçiş bölgesini (Staging Area) ve bilgisayarınızdaki çalışma dizinini (Working Directory) belirtilen commit anına milimetrik olarak geri döndürür. Bu komut çalıştırıldığında, seçilen commit'ten sonra yapılan tüm commit'ler, sahneye eklenen dosyalar ve henüz kaydedilmemiş tüm kod değişiklikleri tamamen silinir.
* **`git revert <commit_ID>`:** Projenin mevcut geçmiş çizgisine dokunmadan, geçmişteki belirli bir commit'in yaptığı değişiklikleri tam tersine çeviren **yeni bir telafi commit'i** oluşturur. Eski commit'leri tarihten silmediği için takım çalışmalarında kullanılan en güvenli geri alma yöntemidir.

---

## 🔍 9. Kod Karşılaştırma (Git Diff)

Projenin farklı aşamaları veya zaman dilimleri arasındaki kod farklarını satır satır incelemek için kullanılır.

* **`git diff`:** Çalışma dizinindeki dosyaların güncel durumu ile son commit arasındaki farkları gösterir. Yalnızca henüz sahneye (`git add`) alınmamış değişiklikleri listeler.
* **`git diff HEAD`:** Bilgisayarınızdaki çalışma dizininde yapılan tüm güncel kod değişikliklerini, durumlarına bakılmaksızın (hem sahneye alınmış hem de alınmamış olanların tamamını) son commit ile karşılaştırır.
* **`git diff <commit_ID_1> <commit_ID_2>`:** Git geçmişindeki iki spesifik commit (zaman dilimi) arasındaki tüm kod farklarını satır satır karşılaştırır. Komut yazılırken commit kimlikleri arasına boşluk bırakılabileceği gibi iki nokta (`..`) işareti de konulabilir.
* **`git diff <brans_adi_1> <brans_adi_2>`:** Belirtilen iki farklı branş arasındaki kod ve yapı farklarını listeler. Branş isimleri arasına boşluk bırakılabileceği gibi iki nokta (`..`) işareti de yerleştirilebilir.

---

## 🛤️ 10. Geçmişi Doğrusallaştırma (Rebase)

* **`git rebase <hedef_brans_adi>`:** Üzerinde çalışılan aktif branşın başlangıç noktasını (kökünü), hedef gösterilen branşın en son commit'ine taşıyarak geçmişi doğrusal (düz bir çizgi halinde) yeniden yazma işlemidir. Bu işlemin temel amacı, proje geçmişini karmaşık dallanmalardan ve gereksiz merge commit'lerinden arındırarak sanki tüm kodlar tek bir hat üzerinde arka arkaya yazılmış gibi tertemiz göstermektir.

---

## ☁️ 11. Uzak Depo Yönetimi (GitHub Entegrasyonu)

Yerel bilgisayarda Git ile yürütülen süreçlerin bulut üzerinde depolanmasını ve takım çalışmasına açılmasını sağlayan platform araçlarıdır.

* **GitHub:** Yazılım geliştiricilerin kodlarını depolamasına, yönetmesine, paylaşmasına ve sürüm kontrolünü sağlamasına olanak tanıyan, Git mimarisini kullanan bulut tabanlı bir iş birliği platformudur.
* **`git remote add origin https://github.com/<kullanici_adi>/<depo_adi>.git`:** Bilgisayardaki yerel Git deposu ile GitHub üzerinde açılmış olan uzak depo arasında dijital bir bağlantı köprüsü kuran temel komuttur.
* **`origin`:** Eklenen uzak sunucu adresinin Git içerisindeki kısa takma adıdır (alias). Küresel standart gereği ana sunucu adresi her zaman `origin` olarak isimlendirilir. Bu sayede her push işleminde uzun internet adresini yazmak yerine bu kısa isim kullanılır.
* **`git push -u origin <brans_adi>`:** Bilgisayardaki kodları GitHub'a ilk kez yüklerken, yerel branş ile uzak sunucudaki branş arasında kalıcı bir takip köprüsü kuran komuttur (Örn: `git push -u origin main` veya `master`).
* **`git push`:** Bilgisayarda yazılan, sahneye alınan (`git add`) ve onaylanan (`git commit`) tüm kod değişikliklerini GitHub'daki uzak sunucuya yükleyen temel komuttur.
* **`git push origin <ozellik_brans_adi>`:** Ana branşın dışındaki diğer yan branşları (Örn: `feat` branşı) GitHub sunucusuna bağımsız olarak yüklemek için kullanılır.
* **Pull Request (PR):** Bir geliştiricinin kendi branşında yazdığı kodları projenin ana branşına (`main`/`master`) eklemek için diğer takım üyelerinden ve proje yöneticilerinden izin, inceleme ve onay talep etmesi sürecidir.
* **`git branch -r`:** Yerel bilgisayarda kayıtlı olan, GitHub tarafındaki tüm uzak branşları (remote branches) listelemek için kullanılan kontrol komuttur.
* **`git fetch origin`:** GitHub'daki tüm yeni değişiklikleri, geçmişi ve branşları kontrol edip bilgisayara indiren ama mevcut canlı kodlarınıza dokunmayan güvenli bir ön izleme komutudur.
* **`git fetch origin master`:** GitHub üzerindeki diğer hiçbir branşa dokunmadan, sadece ve sadece belirtilen branştaki (Örn: `master` veya `main`) yeni commit'leri hedef alarak bilgisayara indiren özel komuttur.
* **`git pull origin <brans_adi>`:** GitHub'daki en güncel kodları ve değişiklikleri bilgisayara indirip mevcut yerel kodlarla otomatik olarak birleştiren eşitleme komutudur (Örn: `git pull origin master`).
* **`git pull = git fetch + git merge`:** `git pull` komutunun arka planda önce verileri indiren (`fetch`), ardından yerel kodla birleştiren (`merge`) iki komutun birleşimi olduğunu gösteren altın formüldür.
* **`git checkout origin/master`:** GitHub üzerindeki branşın en son durumunu yerel bilgisayarda salt okunur bir kopya olarak incelemek ve o ana göz atmak amacıyla kullanılan komuttur.
* **`git clone <adres>`:** GitHub'da duran mevcut bir projenin tüm geçmişini ve dosyalarını bilgisayara ilk kez indirmek için kullanılan temel komuttur. Proje sayfasındaki "Code" butonundan alınan HTTPS veya SSH adresi kullanılır.
* **Fork:** Başka bir kullanıcının veya şirketin hesabındaki bir projenin birebir kopyasını kendi GitHub hesabınıza çıkarma (çatallama) işlemidir.
* **Collaborators (Ortak Çalışanlar):** GitHub üzerinde gizli veya açık bir deponun kodlarına doğrudan müdahale etmesi, kod yazması ve güncelleme (`push`) yapması için depo sahibinin bizzat yetki verdiği diğer yazılımcılardır.
