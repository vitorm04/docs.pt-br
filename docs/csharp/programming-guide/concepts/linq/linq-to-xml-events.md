---
title: "Eventos LINQ to XML (c#) | Microsoft Docs"
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
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Eventos LINQ to XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eventos permitem que você seja notificado quando uma árvore XML é alterada.  
  
 Você pode adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>. O manipulador de eventos em seguida receberá eventos para alterações ao <xref:System.Xml.Linq.XObject> e todos os seus descendentes. Por exemplo, você pode adicionar um manipulador de eventos para a raiz da árvore e lidar com todas as alterações na árvore do manipulador de eventos.  
  
 Para obter exemplos de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eventos, consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.  
  
## Eventos e tipos  
 Use os seguintes tipos ao trabalhar com eventos:  
  
|Tipo|Descrição|  
|----------|---------------|  
|<xref:System.Xml.Linq.XObjectChange>|Especifica o tipo de evento quando um evento é gerado para um <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Fornece dados para o <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed> eventos.|  
  
 Os seguintes eventos são gerados quando você modifica uma árvore XML:  
  
|Evento|Descrição|  
|------------|---------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Ocorre antes deste <xref:System.Xml.Linq.XObject> ou qualquer um de seus descendentes vai mudar.|  
|<xref:System.Xml.Linq.XObject.Changed>|Ocorre quando um <xref:System.Xml.Linq.XObject> foi alterado ou qualquer um de seus descendentes foram alterados.|  
  
## Exemplo  
  
### Descrição  
 Eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML. Por exemplo, convém manter um total de nota fiscal que é a soma dos itens de linha da fatura. Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.  
  
### Código  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### Comentários  
 Esse código produz a seguinte saída:  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## Consulte também  
 [Advanced LINQ to XML Programming \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)