---
title: 'Como: Recuperar uma coleção de elementos (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 0ca40b77a78f155292dfbb26471442450bf16b9b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592644"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Como: Recuperar uma coleção de elementos (LINQ to XML) (C#)
Este tópico demonstra o método de <xref:System.Xml.Linq.XContainer.Elements%2A> . Esse método retorna uma coleção de elementos filho de um elemento.  
  
## <a name="example"></a>Exemplo  
 Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Este exemplo gerencia a seguinte saída.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Consulte também

- [Eixos do LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
