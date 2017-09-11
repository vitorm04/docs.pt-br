---
title: Eventos LINQ to XML (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e2358808dfeafab1576a686563e6025f90e78954
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="89744-102">Eventos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89744-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="89744-103">eventos permitem que você seja notificado quando uma árvore XML é alterada.</span><span class="sxs-lookup"><span data-stu-id="89744-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="89744-104">Você pode adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="89744-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="89744-105">O manipulador de eventos em seguida receberá eventos para alterações ao <xref:System.Xml.Linq.XObject>e todos os seus descendentes.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="89744-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="89744-106">Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="89744-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="89744-107">Para obter exemplos de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eventos, visualizar <xref:System.Xml.Linq.XObject.Changing>e <xref:System.Xml.Linq.XObject.Changed>.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="89744-107">For examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="89744-108">Tipos e eventos</span><span class="sxs-lookup"><span data-stu-id="89744-108">Types and Events</span></span>  
 <span data-ttu-id="89744-109">Você usa os seguintes tipos ao trabalhar com eventos:</span><span class="sxs-lookup"><span data-stu-id="89744-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="89744-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="89744-110">Type</span></span>|<span data-ttu-id="89744-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="89744-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="89744-112"><xref:System.Xml.Linq.XObjectChange></xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="89744-112"><xref:System.Xml.Linq.XObjectChange></span></span>|<span data-ttu-id="89744-113">Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="89744-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="89744-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="89744-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></span></span>|<span data-ttu-id="89744-115">Fornece dados para o <xref:System.Xml.Linq.XObject.Changing>e <xref:System.Xml.Linq.XObject.Changed>eventos.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="89744-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="89744-116">Os seguintes eventos são gerados quando você altera uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="89744-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="89744-117">Evento</span><span class="sxs-lookup"><span data-stu-id="89744-117">Event</span></span>|<span data-ttu-id="89744-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="89744-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89744-119"><xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="89744-119"><xref:System.Xml.Linq.XObject.Changing></span></span>|<span data-ttu-id="89744-120">Ocorre antes deste <xref:System.Xml.Linq.XObject>ou qualquer um de seus descendentes vai mudar.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="89744-120">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<span data-ttu-id="89744-121"><xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changed></span><span class="sxs-lookup"><span data-stu-id="89744-121"><xref:System.Xml.Linq.XObject.Changed></span></span>|<span data-ttu-id="89744-122">Ocorre quando um <xref:System.Xml.Linq.XObject>foi alterado ou qualquer um de seus descendentes foram alterados.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="89744-122">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89744-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89744-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="89744-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="89744-124">Description</span></span>  
 <span data-ttu-id="89744-125">Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="89744-125">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="89744-126">Por exemplo, você pode querer mantém um total de fatura que é a soma das linhas de item de fatura.</span><span class="sxs-lookup"><span data-stu-id="89744-126">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="89744-127">Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.</span><span class="sxs-lookup"><span data-stu-id="89744-127">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89744-128">Código</span><span class="sxs-lookup"><span data-stu-id="89744-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="89744-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="89744-129">Comments</span></span>  
 <span data-ttu-id="89744-130">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="89744-130">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89744-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89744-131">See Also</span></span>  
 [<span data-ttu-id="89744-132">Avançada LINQ to XML programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89744-132">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
