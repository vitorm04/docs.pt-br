---
title: "Como projetar um tipo anônimo (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 31e0b9c5714c2365323d8c8f65659ee1b1ef5e2b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-project-an-anonymous-type-c"></a>Como projetar um tipo anônimo (C#)
Em alguns casos você pode querer projetar uma consulta a um novo tipo, mesmo que você soubesse que você usará apenas este tipo para um curto quando. É muito trabalho adicional para criar apenas um novo tipo para usar na projeção. Uma abordagem mais eficiente nesse caso é projeto para um tipo anônimo. Tipos anônimos permitem que você defina uma classe, então declare e inicialize um objeto de aquela classe, sem dar um nome para a classe.  
  
 Os tipos anônimos são a implementação de C# do conceito matemático de uma *tupla*. O tuple o termo matemático proveniente da sequência única, double, triplo, quádruplo, quintuple, n- tuple. Refere-se a uma sequência finito rotuladas de objetos, cada um de um tipo específico. Isso é às vezes chamado uma lista de pares nome/valor. Por exemplo, o conteúdo de um endereço no documento XML [Arquivo XML de exemplo: pedido de compra típico (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) pode ser expresso da seguinte maneira:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Quando você cria uma instância de um tipo anônimo, é conveniente pensar nele como criar um tuple de Em ordem. Se você escrever uma consulta que cria um tuple na cláusula `select` , a consulta retorna `IEnumerable` de tuple.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a cláusula de `select` projetos de um tipo anônimo. O exemplo usa em `var` para criar o objeto de `IEnumerable` . Dentro do loop de `foreach` , a variável de iteração torna-se em uma instância do tipo anônimo criado na expressão de consulta.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 Esse código gera a seguinte saída:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

