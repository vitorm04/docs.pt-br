---
title: Como recuperar um único atributo (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 55da36099af72259a4e72205f142ab855f000c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321282"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="73077-102">Como recuperar um único atributo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="73077-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="73077-103">Este tópico explica como recuperar um único atributo de um elemento, dado o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="73077-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="73077-104">Isso é útil para gravar as expressões de consulta onde você deseja localizar um elemento que possui um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="73077-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="73077-105">O método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement> retorna <xref:System.Xml.Linq.XAttribute> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="73077-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73077-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73077-106">Example</span></span>  
 <span data-ttu-id="73077-107">O exemplo a seguir usa o método <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="73077-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="73077-108">Este exemplo localiza os descendentes na árvore chamada `Phone`, e localiza o atributo chamado `type`.</span><span class="sxs-lookup"><span data-stu-id="73077-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="73077-109">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="73077-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="73077-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73077-110">Example</span></span>  
 <span data-ttu-id="73077-111">Se você deseja recuperar o valor do atributo, você pode convertê-lo, exatamente como você faz para com objetos de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="73077-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="73077-112">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="73077-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="73077-113">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="73077-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="73077-114"> fornece operadores cast explícitos para a classe <xref:System.Xml.Linq.XAttribute> para `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="73077-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73077-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73077-115">Example</span></span>  
 <span data-ttu-id="73077-116">O exemplo a seguir mostra o mesmo código para um atributo que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="73077-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="73077-117">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="73077-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="73077-118">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="73077-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="73077-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73077-119">See Also</span></span>  
 [<span data-ttu-id="73077-120">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="73077-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
