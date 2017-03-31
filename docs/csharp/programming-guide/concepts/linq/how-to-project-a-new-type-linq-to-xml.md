---
title: Como projetar um novo tipo (LINQ to XML) (C#) | Microsoft Docs
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
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1aa8c4676890dcc25108d919a501bde44299db04
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Como projetar um novo tipo (LINQ to XML) (C#)
Outros exemplos nesta seção mostraram consultas que retornam resultados como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` e <xref:System.Collections.Generic.IEnumerable%601> de `int`. Esses são tipos comuns de resultado, mas não são adequados para cada cenário. Em muitos casos você desejará que suas consultas retornem um <xref:System.Collections.Generic.IEnumerable%601> de algum outro tipo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como instanciar objetos na cláusula `select` . O código define primeiro uma nova classe com um construtor, e altera a declaração de `select` de modo que a expressão é uma nova instância da nova classe.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
  
        IEnumerable<NameQty> nqList =  
            from n in po.Descendants("Item")  
            select new NameQty(  
                    (string)n.Element("ProductName"),  
                    (int)n.Element("Quantity")  
                );  
  
        foreach (NameQty n in nqList)  
            Console.WriteLine(n.name + ":" + n.qty);  
    }  
}  
```  
  
 Este exemplo usa o método `M:System.Xml.Linq.XElement.Element` que foi apresentado no tópico [Como recuperar um único elemento filho (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de `M:System.Xml.Linq.XElement.Element` .  
  
 Este exemplo gera a seguinte saída:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
