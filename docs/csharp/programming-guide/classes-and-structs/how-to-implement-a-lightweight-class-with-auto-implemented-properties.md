---
title: 'Nasıl yapılır: Otomatik Uygulanan Özelliklerle Hafif bir Sınıf Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 9612ec916481776691e85a84503ce5063c20b099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Nasıl yapılır: Otomatik Uygulanan Özelliklerle Hafif bir Sınıf Uygulama (C# Programlama Kılavuzu)
Bu örnek yalnızca otomatik uygulanan özellikler kümesi kapsülleyen hizmet veren değişmez hafif bir sınıf oluşturulacağını gösterir. Başvuru türü anlamları kullandığınızda, bu tür bir yapı yapı yerine kullanın.  
  
 Bir sabit özelliği iki şekilde yapabilirsiniz.  Bildirebilirsiniz [ayarlamak](../../../csharp/language-reference/keywords/set.md) accessor.to olması [özel](../../../csharp/language-reference/keywords/private.md).  Özellik yalnızca türü içinde ayarlanabilir, ancak tüketicilere sabittir.  Bunun yerine yalnızca bildirebilir [almak](../../../csharp/language-reference/keywords/get.md) özelliği tür oluşturucusundaki her yerde dışında değişmez yapar erişimcisi.  
  
 Bildirme ne zaman özel `set` erişimci özelliği başlatmak için nesne Başlatıcı kullanamazsınız. Bir oluşturucu ya da bir fabrika yöntemini kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, otomatik uygulanan özellikler sahip değişmez bir sınıf uygulama için iki yol gösterir. Özel özelliklerle birini her bildirir `set` ve özelliklere sahip bir `get` yalnızca.  Birinci sınıf kullandığı özellikler ve ikinci sınıfı yalnızca başlatmak için bir oluşturucu bir oluşturucu çağıran bir statik fabrika yöntemi kullanır.  
  
```csharp  
// This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // constructor to initialize its properties.   
    class Contact  
    {  
        // Read-only properties.   
        public string Name { get; }  
        public string Address { get; private set; }  
  
        // Public constructor.   
        public Contact(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
    }  
  
    // This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // static method and private constructor to initialize its properties.      
    public class Contact2  
    {  
        // Read-only properties.   
        public string Name { get; private set; }  
        public string Address { get; }  
  
        // Private constructor.   
        private Contact2(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
  
        // Public factory method.   
        public static Contact2 CreateContact(string name, string address)  
        {  
            return new Contact2(name, address);  
        }  
    }  
  
    public class Program  
    {   
        static void Main()  
        {  
            // Some simple data sources.   
            string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",   
                              "Cesar Garcia", "Debra Garcia"};  
            string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",  
                                  "12 108th St.", "89 E. 42nd St."};  
  
            // Simple query to demonstrate object creation in select clause.   
            // Create Contact objects by using a constructor.   
            var query1 = from i in Enumerable.Range(0, 5)  
                        select new Contact(names[i], addresses[i]);  
  
            // List elements cannot be modified by client code.   
            var list = query1.ToList();  
            foreach (var contact in list)  
            {  
                Console.WriteLine("{0}, {1}", contact.Name, contact.Address);  
            }  
  
            // Create Contact2 objects by using a static factory method.   
            var query2 = from i in Enumerable.Range(0, 5)  
                         select Contact2.CreateContact(names[i], addresses[i]);  
  
            // Console output is identical to query1.   
            var list2 = query2.ToList();  
  
            // List elements cannot be modified by client code.   
            // CS0272:   
            // list2[0].Name = "Eugene Zabokritski";   
  
            // Keep the console open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();                  
        }  
    }  
  
/* Output:  
    Terry Adams, 123 Main St.  
    Fadi Fakhouri, 345 Cypress Ave.  
    Hanying Feng, 678 1st Ave  
    Cesar Garcia, 12 108th St.  
    Debra Garcia, 89 E. 42nd St.  
*/  
```  
  
 Derleyici her otomatik uygulanan bir özellik için yedekleme alanları oluşturur. Alanlar doğrudan kaynak kodundan erişilebilir değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
