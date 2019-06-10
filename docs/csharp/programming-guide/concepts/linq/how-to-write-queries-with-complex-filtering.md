---
title: 'Como: Escrever consultas com filtragem complexa (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7a90a754036008463646321a3e9b9b7d83a3be33
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484590"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Como: Escrever consultas com filtragem complexa (C#)
Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos. Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos. Este tópico dá um exemplo de como escrever uma consulta com filtragem complexa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como localizar todos os elementos `PurchaseOrder` que têm um elemento filho `Address` que têm um atributo `Type` igual a “Shipping” e um elemento filho `State` igual a “NY”. Ele usa uma consulta aninhada na cláusula `Where` e o operador `Any` retornará `true` se a coleção tiver elementos nele. Para obter informações sobre como usar a sintaxe de consulta baseada em método, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Para obter mais informações sobre o operador `Any`, consulte [Operações de quantificador (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
99505  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
99505  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Operações de projeção (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Operações de quantificador (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
