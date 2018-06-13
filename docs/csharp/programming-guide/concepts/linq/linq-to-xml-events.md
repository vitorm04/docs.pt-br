---
title: Eventos LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 3dd4eaa0261ae7d878e188572d260b34b64fc031
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322387"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="15e35-102">Eventos LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="15e35-102">LINQ to XML Events (C#)</span></span>
<span data-ttu-id="15e35-103">Eventos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem que você seja notificado quando uma árvore XML é modificada.</span><span class="sxs-lookup"><span data-stu-id="15e35-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="15e35-104">Você pode adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="15e35-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="15e35-105">O manipulador de eventos em receberá eventos para alterações ao <xref:System.Xml.Linq.XObject> e a qualquer um dos seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="15e35-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="15e35-106">Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="15e35-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="15e35-107">Para exemplos de eventos de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="15e35-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="15e35-108">Tipos e eventos</span><span class="sxs-lookup"><span data-stu-id="15e35-108">Types and Events</span></span>  
 <span data-ttu-id="15e35-109">Você usa os seguintes tipos ao trabalhar com eventos:</span><span class="sxs-lookup"><span data-stu-id="15e35-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="15e35-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="15e35-110">Type</span></span>|<span data-ttu-id="15e35-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="15e35-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="15e35-112">Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="15e35-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="15e35-113">Fornece dados para os eventos de <xref:System.Xml.Linq.XObject.Changing> e de <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="15e35-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="15e35-114">Os seguintes eventos são gerados quando você altera uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="15e35-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="15e35-115">evento</span><span class="sxs-lookup"><span data-stu-id="15e35-115">Event</span></span>|<span data-ttu-id="15e35-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="15e35-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="15e35-117">Ocorre antes deste <xref:System.Xml.Linq.XObject> ou alguns dos seus descendentes são indo alterar.</span><span class="sxs-lookup"><span data-stu-id="15e35-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="15e35-118">Ocorre quando <xref:System.Xml.Linq.XObject> alterar ou alguns dos seus descendentes alterado.</span><span class="sxs-lookup"><span data-stu-id="15e35-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="15e35-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15e35-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="15e35-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="15e35-120">Description</span></span>  
 <span data-ttu-id="15e35-121">Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="15e35-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="15e35-122">Por exemplo, você pode querer mantém um total de fatura que é a soma das linhas de item de fatura.</span><span class="sxs-lookup"><span data-stu-id="15e35-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="15e35-123">Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.</span><span class="sxs-lookup"><span data-stu-id="15e35-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="15e35-124">Código</span><span class="sxs-lookup"><span data-stu-id="15e35-124">Code</span></span>  
  
```csharp  
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
  
### <a name="comments"></a><span data-ttu-id="15e35-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="15e35-125">Comments</span></span>  
 <span data-ttu-id="15e35-126">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="15e35-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15e35-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15e35-127">See Also</span></span>  
 [<span data-ttu-id="15e35-128">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="15e35-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
