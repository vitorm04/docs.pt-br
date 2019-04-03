---
title: 'Como: Projetar um tipo anônimo (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: cc8e59ac1037fc173cb44d8c8ff344374c5766ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834563"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Como: Projetar um tipo anônimo (Visual Basic)
Em alguns casos você pode querer projetar uma consulta a um novo tipo, mesmo que você soubesse que você usará apenas este tipo para um curto quando. É muito trabalho adicional para criar apenas um novo tipo para usar na projeção. Uma abordagem mais eficiente nesse caso é projeto para um tipo anônimo. Tipos anônimos permitem que você defina uma classe, então declare e inicialize um objeto de aquela classe, sem dar um nome para a classe.  
  
 Os tipos anônimos são a implementação de C# do conceito matemático de uma *tupla*. O tuple o termo matemático proveniente da sequência única, double, triplo, quádruplo, quintuple, n- tuple. Refere-se a uma sequência finito rotuladas de objetos, cada um de um tipo específico. Isso é às vezes chamado uma lista de pares nome/valor. Por exemplo, o conteúdo de um endereço no documento XML [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) pode ser expresso da seguinte maneira:  
  
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
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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

- [Projeções e transformações (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
