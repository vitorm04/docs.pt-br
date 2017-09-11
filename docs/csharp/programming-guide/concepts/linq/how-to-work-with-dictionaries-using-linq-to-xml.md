---
title: "Como trabalhar com dicionários usando LINQ to XML (C#)"
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
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66668c14c472f68dd3da365bd7c7cbc64ccd4365
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="4f258-102">Como trabalhar com dicionários usando LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4f258-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="4f258-103">É conveniente converter variedades de estruturas de dados para XML, e XML de volta para outras estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="4f258-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="4f258-104">Este tópico mostra uma implementação específica dessa abordagem geral convertendo <xref:System.Collections.Generic.Dictionary%602> a XML e verso.</span><span class="sxs-lookup"><span data-stu-id="4f258-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f258-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f258-105">Example</span></span>  
 <span data-ttu-id="4f258-106">Este exemplo usa um formulário de compilação funcional em que uma consulta projetos novos objetos de <xref:System.Xml.Linq.XElement> e a coleção resultante é passada como um argumento para o construtor do objeto de <xref:System.Xml.Linq.XElement> raiz.</span><span class="sxs-lookup"><span data-stu-id="4f258-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="4f258-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4f258-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="4f258-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f258-108">Example</span></span>  
 <span data-ttu-id="4f258-109">O código a seguir cria um dicionário XML.</span><span class="sxs-lookup"><span data-stu-id="4f258-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="4f258-110">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4f258-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f258-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f258-111">See Also</span></span>  
 [<span data-ttu-id="4f258-112">Projeções e transformações (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4f258-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

