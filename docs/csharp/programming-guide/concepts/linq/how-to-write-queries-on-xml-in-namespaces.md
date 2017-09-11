---
title: Como escrever consultas no XML nos namespaces (C#)
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
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 54d8c876ca5f8c6d721eaab13515e70f23a68744
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="5eefd-102">Como escrever consultas no XML nos namespaces (C#)</span><span class="sxs-lookup"><span data-stu-id="5eefd-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="5eefd-103">Para escrever uma consulta em XML que está em um namespace, você deve usar os objetos <xref:System.Xml.Linq.XName> que têm o namespace correto.</span><span class="sxs-lookup"><span data-stu-id="5eefd-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="5eefd-104">Para C#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, em seguida, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.</span><span class="sxs-lookup"><span data-stu-id="5eefd-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="5eefd-105">O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="5eefd-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="5eefd-106">O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="5eefd-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eefd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eefd-107">Example</span></span>  
 <span data-ttu-id="5eefd-108">O exemplo a seguir cria uma árvore XML que está em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="5eefd-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="5eefd-109">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="5eefd-109">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="5eefd-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5eefd-110">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="5eefd-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eefd-111">Example</span></span>  
 <span data-ttu-id="5eefd-112">No C#, você escreve consultas da mesma forma independentemente se estiver escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="5eefd-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="5eefd-113">O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="5eefd-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="5eefd-114">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="5eefd-114">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="5eefd-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5eefd-115">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eefd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eefd-116">See Also</span></span>  
 [<span data-ttu-id="5eefd-117">Trabalhando com namespaces XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5eefd-117">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

