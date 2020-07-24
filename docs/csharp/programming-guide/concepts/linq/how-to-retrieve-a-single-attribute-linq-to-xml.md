---
title: Como recuperar um único atributo (LINQ to XML) (C#)
description: Saiba como usar LINQ to XML recuperar um único atributo de um elemento em C#, dado o nome do atributo.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103438"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="b6e8f-103">Como recuperar um único atributo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b6e8f-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b6e8f-104">Este tópico explica como recuperar um único atributo de um elemento, dado o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="b6e8f-105">Isso é útil para gravar as expressões de consulta onde você deseja localizar um elemento que possui um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="b6e8f-106">O método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement> retorna <xref:System.Xml.Linq.XAttribute> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e8f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6e8f-107">Example</span></span>  
 <span data-ttu-id="b6e8f-108">O exemplo a seguir usa o método <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="b6e8f-109">Este exemplo localiza os descendentes na árvore chamada `Phone`, e localiza o atributo chamado `type`.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="b6e8f-110">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b6e8f-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="b6e8f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6e8f-111">Example</span></span>  
 <span data-ttu-id="b6e8f-112">Se você deseja recuperar o valor do atributo, você pode convertê-lo, exatamente como você faz para com objetos de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b6e8f-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b6e8f-113">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-113">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="b6e8f-114">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b6e8f-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b6e8f-115">fornece operadores cast explícitos para a classe <xref:System.Xml.Linq.XAttribute> para `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e8f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6e8f-116">Example</span></span>  
 <span data-ttu-id="b6e8f-117">O exemplo a seguir mostra o mesmo código para um atributo que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b6e8f-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="b6e8f-118">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6e8f-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b6e8f-119">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b6e8f-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6e8f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6e8f-120">See also</span></span>

- [<span data-ttu-id="b6e8f-121">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b6e8f-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
