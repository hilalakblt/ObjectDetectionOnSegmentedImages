# U-net Model İle Segmentasyon Yapılmış Görüntülerin Eğitimi ve Nesne Tespiti 


KITTI Datasetinde bulunan train ve test verileri kullanılmıştır. Toplamda 175 train verisi ve 25 test verisi bulunmaktadır. Görüntüler ilk olarak ön işlemden geçirilerek (128, 128) size olacak şekilde ayarlanmış ve normalizasyon işlemi uygulanmıştır. Sonrasında train verilerinin bir kısmı validasyon verileri olarak ayrılmıştır. Burada 140 train ve 35 validasyon verisi olarak kullanacağız.

Eğitme işlemi için U-net model kullanılmıştır. Parametrelerim lr = 0.005, loss = binary_crossentropy, metrics = accuracy ve epochs = 200 olarak verilmiştir.

Model eğitildikten sonra accuracy = %79 ve loss = %60 olarak elde edilmiştir. Örnek veriler aşağıdaki şekildedir:

Test

<img width="261" alt="Ekran Resmi 2023-03-23 12 30 49" src="https://user-images.githubusercontent.com/75835998/227161095-83764143-c7b2-4280-880e-d015e565125c.png">


Ground Truth

<img width="261" alt="Ekran Resmi 2023-03-22 22 04 57" src="https://user-images.githubusercontent.com/75835998/227158884-3c815375-2ecb-40ef-a7d2-f5f9c2699bc5.png">

Prediction

<img width="261" alt="Ekran Resmi 2023-03-22 22 03 18" src="https://user-images.githubusercontent.com/75835998/227158908-7e47c081-e22d-4201-be09-63aa048c9f9e.png">


Tahmin verileri elde edildikten sonra tespitini yapmak istediğim nesnenin RGB değerini bularak eldeki görüntüde pixeller içerisinde bu rengi arama işlemi gerçekleştirdim. Bunu yapabilmek için ise OpenCV kütüphanesinin inRange() fonksiyonundan yararlandım. Bu fonksiyon ile görüntü içerisinde istediğim RGB değerinin pixel pozisyonunu bulabildim. Daha sonra nesnenin bounding boxını çizebilmek için yine OpenCV nin rectangle() fonksiyonundan yararlandım. Örnek sonuçlar aşağıdaki şekildedir:





<img width="261" alt="Ekran Resmi 2023-03-23 12 40 26" src="https://user-images.githubusercontent.com/75835998/227163615-ad57fef5-6380-4ad2-9e2c-f0672c944d95.png"><img width="261" alt="Ekran Resmi 2023-03-22 22 02 51" src="https://user-images.githubusercontent.com/75835998/227163676-8c7eca43-9452-4adf-90ca-65164345f138.png"><img width="261" alt="Ekran Resmi 2023-03-22 22 25 20" src="https://user-images.githubusercontent.com/75835998/227163750-f545b209-fad3-4774-a787-ae986e153ba8.png">



