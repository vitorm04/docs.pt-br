---
title: "Como implementar uma classe leve com propriedades autoimplementadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "propriedades autoimplementadas [C#]"
  - "propriedades [C#], autoimplementadas"
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar uma classe leve com propriedades autoimplementadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como criar uma classe leve imutável que serve apenas para encapsular um conjunto de propriedades implementadas automaticamente.  Use esse tipo de construção em vez de uma estrutura quando você deve usar a semântica do tipo de referência.  
  
 Você pode fazer uma propriedade imutável de duas maneiras.  Você pode declarar o [definir](../../../csharp/language-reference/keywords/set.md) accessor.to ser [particular](../../../csharp/language-reference/keywords/private.md).  A propriedade só é configurável dentro do tipo, mas é imutável aos consumidores.  Em vez disso, pode declarar somente o [obter](../../../csharp/language-reference/keywords/get.md) acessador, o que torna a propriedade imutáveis em todos os lugares, exceto no construtor do tipo.  
  
 Quando você declara uma privada `set` acessador, você não pode usar um inicializador de objeto para inicializar a propriedade.  Você deve usar um construtor ou um método de fábrica.  
  
## Exemplo  
 O exemplo a seguir mostra duas maneiras de implementar uma classe imutável que tem propriedades implementadas automaticamente.  Cada forma declara uma das propriedades com uma privada `set` e uma das propriedades com um `get` somente.  A primeira classe usa um construtor somente para inicializar as propriedades e a segunda classe usa um método de fábrica estáticos que chama um construtor.  
  
```c#  
// This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // constructor to initialize its properties.   
    class Contact  
    {  
        // Read-only properties.   
        public string Name { get; }  
        public string Address { get; private set; }  
  
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
    public class Contact2  
    {  
        // Read-only properties.   
        public string Name { get; private set; }  
        public string Address { get; }  
  
        // Private constructor.   
        private Contact2(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
  
        // Public factory method.   
        public static Contact2 CreateContact(string name, string address)  
        {  
            return new Contact2(name, address);  
        }  
    }  
  
    public class Program  
    {   
        static void Main()  
        {  
            // Some simple data sources.   
            string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",   
                              "Cesar Garcia", "Debra Garcia"};  
            string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",  
                                  "12 108th St.", "89 E. 42nd St."};  
  
            // Simple query to demonstrate object creation in select clause.   
            // Create Contact objects by using a constructor.   
            var query1 = from i in Enumerable.Range(0, 5)  
                        select new Contact(names[i], addresses[i]);  
  
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
  
 O compilador cria campos de backup para cada propriedade implementada automaticamente.  Os campos não são acessíveis diretamente do código\-fonte.  
  
## Consulte também  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)