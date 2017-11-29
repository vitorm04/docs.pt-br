---
title: Como localizar descendentes de um elemento filho (XPath-LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 873cfe6a725a932ac4616e7ccf0ea11e3f6479f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="99dc4-102">Como localizar descendentes de um elemento filho (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="99dc4-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="99dc4-103">Este tópico mostra como obter os elementos descendentes de um elemento filho com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="99dc4-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="99dc4-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="99dc4-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="99dc4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99dc4-105">Example</span></span>  
 <span data-ttu-id="99dc4-106">Este exemplo simula problemas de extrair o texto de uma representação de um documento de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="99dc4-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="99dc4-107">Seleciona primeiro todos os elementos de `Paragraph` , e então seleciona todos os elementos descendentes de `Text` de cada elemento de `Paragraph` .</span><span class="sxs-lookup"><span data-stu-id="99dc4-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="99dc4-108">Isso não selecionar os elementos de `Text` descendente do elemento de `Comment` .</span><span class="sxs-lookup"><span data-stu-id="99dc4-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="99dc4-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="99dc4-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="99dc4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99dc4-110">See Also</span></span>  
 [<span data-ttu-id="99dc4-111">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="99dc4-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
