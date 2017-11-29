---
title: Eventos LINQ to XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19d8f19f9feb1d385f9900d76d2a7af8e89bbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-visual-basic"></a>Eventos LINQ to XML (Visual Basic)
Eventos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem que você seja notificado quando uma árvore XML é modificada.  
  
 Você pode adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>. O manipulador de eventos em receberá eventos para alterações ao <xref:System.Xml.Linq.XObject> e a qualquer um dos seus descendentes. Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.  
  
 Para exemplos de eventos de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Tipos e eventos  
 Você usa os seguintes tipos ao trabalhar com eventos:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Fornece dados para os eventos de <xref:System.Xml.Linq.XObject.Changing> e de <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Os seguintes eventos são gerados quando você altera uma árvore XML:  
  
|Evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Ocorre antes deste <xref:System.Xml.Linq.XObject> ou alguns dos seus descendentes são indo alterar.|  
|<xref:System.Xml.Linq.XObject.Changed>|Ocorre quando <xref:System.Xml.Linq.XObject> alterar ou alguns dos seus descendentes alterado.|  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML. Por exemplo, você pode querer mantém um total de fatura que é a soma das linhas de item de fatura. Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.  
  
### <a name="code"></a>Código  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Comentários  
 Esse código gera a seguinte saída:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Avançada LINQ to XML programação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
