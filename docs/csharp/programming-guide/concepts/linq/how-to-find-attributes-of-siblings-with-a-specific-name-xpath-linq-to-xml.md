---
title: Como localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (C#)
description: Saiba como localizar todos os atributos dos irmãos do nó de contexto. Examine um exemplo de código que usa um arquivo XML de exemplo.
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 12bba22c91fef92fc3383d028ff9dfb8bd3cfa3e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301691"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="d0bc8-104">Como localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0bc8-104">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d0bc8-105">Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="d0bc8-105">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="d0bc8-106">Somente os atributos com um nome específico são retornados na coleção.</span><span class="sxs-lookup"><span data-stu-id="d0bc8-106">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="d0bc8-107">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="d0bc8-107">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="d0bc8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0bc8-108">Example</span></span>  
 <span data-ttu-id="d0bc8-109">Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`.</span><span class="sxs-lookup"><span data-stu-id="d0bc8-109">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="d0bc8-110">O resultado é uma coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="d0bc8-110">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="d0bc8-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d0bc8-111">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d0bc8-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d0bc8-112">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  