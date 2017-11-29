---
title: "Como implementar uma classe leve com propriedades autoimplementadas (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f43dfaffe6ff696387573729dc25cabe33c1fede
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="0e40b-102">Como implementar uma classe leve com propriedades autoimplementadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0e40b-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="0e40b-103">Este exemplo mostra como criar uma classe leve imutável que serve apenas para encapsular um conjunto de propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="0e40b-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="0e40b-104">Use esse tipo de constructo em vez de um struct quando for necessário usar a semântica do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="0e40b-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>  
  
 <span data-ttu-id="0e40b-105">É possível fazer uma propriedade imutável de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="0e40b-105">You can make an immutable property in two ways.</span></span>  <span data-ttu-id="0e40b-106">É possível declarar o acessador [set](../../../csharp/language-reference/keywords/set.md) como [privado](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="0e40b-106">You can declare the [set](../../../csharp/language-reference/keywords/set.md) accessor.to be [private](../../../csharp/language-reference/keywords/private.md).</span></span>  <span data-ttu-id="0e40b-107">A propriedade será configurável somente dentro do tipo, mas será imutável para os consumidores.</span><span class="sxs-lookup"><span data-stu-id="0e40b-107">The property is only settable within the type, but it is immutable to consumers.</span></span>  <span data-ttu-id="0e40b-108">Em vez disso, é possível declarar somente o acessador [get](../../../csharp/language-reference/keywords/get.md), o que torna a propriedade imutável em todos os lugares, exceto no construtor do tipo.</span><span class="sxs-lookup"><span data-stu-id="0e40b-108">You can instead declare only the [get](../../../csharp/language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>  
  
 <span data-ttu-id="0e40b-109">Ao declarar um acessador privado `set`, não é possível usar um inicializador de objeto para inicializar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="0e40b-109">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="0e40b-110">É necessário usar um construtor ou um método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="0e40b-110">You must use a constructor or a factory method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e40b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e40b-111">Example</span></span>  
 <span data-ttu-id="0e40b-112">O exemplo a seguir mostra duas maneiras de implementar uma classe imutável que tem propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="0e40b-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="0e40b-113">Entre essas maneiras, uma declara uma das propriedades com um `set` privado e outra declara uma das propriedades somente com um `get`.</span><span class="sxs-lookup"><span data-stu-id="0e40b-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="0e40b-114">A primeira classe usa um construtor somente para inicializar as propriedades e a segunda classe usa um método de fábrica estático que chama um construtor.</span><span class="sxs-lookup"><span data-stu-id="0e40b-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>  
  
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
  
 <span data-ttu-id="0e40b-115">O compilador cria campos de suporte para cada propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="0e40b-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="0e40b-116">Os campos não são acessíveis diretamente do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0e40b-116">The fields are not accessible directly from source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e40b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e40b-117">See Also</span></span>  
 [<span data-ttu-id="0e40b-118">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0e40b-118">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="0e40b-119">struct</span><span class="sxs-lookup"><span data-stu-id="0e40b-119">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="0e40b-120">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="0e40b-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
