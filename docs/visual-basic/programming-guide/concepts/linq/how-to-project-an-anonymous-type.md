---
title: "Como: projeto de um tipo anônimo (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a9edd260e9bc36449445ee835648573c7bc9c229
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Como: projeto de um tipo anônimo (Visual Basic)
Em alguns casos você pode querer projetar uma consulta a um novo tipo, mesmo que você soubesse que você usará apenas este tipo para um curto quando. É muito trabalho adicional para criar apenas um novo tipo para usar na projeção. Uma abordagem mais eficiente nesse caso é projeto para um tipo anônimo. Tipos anônimos permitem que você defina uma classe, então declare e inicialize um objeto de aquela classe, sem dar um nome para a classe.  
  
 Tipos anônimos são a implementação do c# do conceito matemático de um *tupla*. O tuple o termo matemático proveniente da sequência única, double, triplo, quádruplo, quintuple, n- tuple. Refere-se a uma sequência finito rotuladas de objetos, cada um de um tipo específico. Isso é às vezes chamado uma lista de pares nome/valor. Por exemplo, o conteúdo de um endereço no [arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) documento XML pode ser expressa da seguinte maneira:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Quando você cria uma instância de um tipo anônimo, é conveniente pensar nele como criar um tuple de Em ordem. Se você escrever uma consulta que cria um tuple na cláusula `Select` , a consulta retorna `IEnumerable` de tuple.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a cláusula de `Select` projetos de um tipo anônimo. O exemplo usa em `Dim` para criar o objeto de `IEnumerable` . Dentro do loop de `For Each` , a variável de iteração torna-se em uma instância do tipo anônimo criado na expressão de consulta.  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
  
```  
  
 Esse código gera a seguinte saída:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
