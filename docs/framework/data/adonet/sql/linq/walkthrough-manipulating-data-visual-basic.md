---
title: 'İzlenecek yol: Veri (Visual Basic) düzenleme'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: e0bf8b32595f656d3bff424610f193bd84d0f5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>İzlenecek yol: Veri (Visual Basic) düzenleme
Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryosu ekleme, değiştirme ve bir veritabanındaki verileri silme. Bir müşteri ekleyin, bir müşterinin adını değiştirin ve sipariş silmek için örnek Northwind veritabanının bir kopyasını kullanır.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuz aşağıdakileri gerektirir:  
  
-   Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest2") kullanılır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosyasını c:\linqtest2 klasörüne kopyalayın.  
  
-   Northwind veritabanından oluşturulan Visual Basic kod dosyası.  
  
     Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı. Bu kılavuz, aşağıdaki komut satırı ile SQLMetal aracı kullanılarak yazılmış olduğundan:  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
     Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'da çözüm.  
  
-   Veritabanı kod dosyası projesine ekleniyor.  
  
-   Yeni bir müşteri nesnesi oluşturma.  
  
-   Bir müşterinin ilgili kişi adı değiştirme.  
  
-   Bir sipariş siliniyor.  
  
-   Bu değişiklikler Northwind veritabanına gönderiliyor.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1.  Visual Studio üzerinde **dosya** menüsünde tıklatın **yeni proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual Basic**.  
  
3.  İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **LinqDataManipulationApp**.  
  
5.  **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır. Varsa `System.Data.Linq` projenizdeki bir başvuru olarak listelenmemiş (tıklatın **tüm dosyaları göster** içinde **Çözüm Gezgini** ve genişletin **başvuruları** düğüm), açıklandığı gibi eklemek Aşağıdaki adımlar.  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.  
  
     Derleme projeye eklenir.  
  
3.  Kod Düzenleyicisi'nde, yukarıdaki aşağıdaki yönergeleri eklemek **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleme  
 Bu adımlarda, SQLMetal aracı Northwind örnek veritabanı'ndaki bir kod dosyası oluşturmak için kullandığınız varsayılır. Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2.  İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest2\northwind.vb gidin ve ardından **Ekle**.  
  
     Northwind.vb dosyası projeye eklenir.  
  
## <a name="setting-up-the-database-connection"></a>Veritabanı bağlantısı kurma  
 İlk olarak, veritabanı bağlantınızı test edin. Özellikle Northwnd, veritabanının adını hiçbir i olduğuna dikkat edin karakter. Sonraki adımlarda hatalara neden Northwind parçalı sınıf nasıl yazıldığını belirlemek için northwind.vb dosyasını gözden geçirin.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Ayarlama ve veritabanı bağlantısını test etme  
  
1.  Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Bu noktada uygulamayı test etmek için F5 tuşuna basın.  
  
     A **konsol** penceresi açılır.  
  
     Enter tuşuna basarak uygulamayı kapatmak **konsol** penceresinde veya tıklatarak **durdurma hata ayıklama** Visual Studio üzerinde **hata ayıklama** menüsü.  
  
## <a name="creating-a-new-entity"></a>Yeni bir varlık oluşturma  
 Yeni bir varlık oluşturma basittir. Nesne oluşturma (gibi `Customer`) kullanarak `New` anahtar sözcüğü.  
  
 Bu ve aşağıdaki bölümlerde, yalnızca yerel önbelleğe değişiklikler yapıyor. Çağrısı tamamlanana kadar hiçbir değişiklik veritabanına gönderilen <xref:System.Data.Linq.DataContext.SubmitChanges%2A> bu kılavuzda sonuna doğru.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Yeni bir müşteri varlık nesnesini eklemek için  
  
1.  Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine` içinde `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresinde gösterilen sonuçları aşağıdaki gibidir:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Yeni satır sonuçlarında görünmez unutmayın. Yeni veriler veritabanına henüz gönderilmedi.  
  
3.  Enter tuşuna basın **konsol** penceresi hata ayıklamayı durdurun.  
  
## <a name="updating-an-entity"></a>Bir varlık güncelleştiriliyor  
 Aşağıdaki adımlarda, alacak bir `Customer` nesne ve özelliklerinden biri değiştirin.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Bir müşterinin adını değiştirmek için  
  
-   Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Bir varlığı silme  
 Aynı müşteri nesnesini kullanarak, ilk sipariş silebilirsiniz.  
  
 Aşağıdaki kod ilişkileri sever gösterilmiştir satırları ve satır veritabanından silmek nasıl arasında.  
  
#### <a name="to-delete-a-row"></a>Bir satır silmek için  
  
-   Aşağıdaki kodu ekleyin yukarıdaki `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Veritabanı değişiklikleri gönderme  
 Son adım gereklidir oluşturmak için güncelleştirme ve nesneleri silme gerçekte değişiklikler veritabanına göndermek için. Bu adım olmadan yaptığınız değişiklikler yalnızca yerel ve sorgu sonuçlarında görünmez.  
  
#### <a name="to-submit-changes-to-the-database"></a>Değişiklikler veritabanına göndermek için  
  
1.  Aşağıdaki kod yalnızca yukarıda INSERT `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve sonra değişiklikleri gönderme etkilerini:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresinde aşağıdaki gibi görünür:  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  Enter tuşuna basın **konsol** penceresi hata ayıklamayı durdurun.  
  
> [!NOTE]
>  Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemiyor yeniden olduğu gibi aynı müşteriye yeniden eklenemiyor çünkü. Çözümü yeniden yürütmek için eklenecek Müşteri Kimliği değerini değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
