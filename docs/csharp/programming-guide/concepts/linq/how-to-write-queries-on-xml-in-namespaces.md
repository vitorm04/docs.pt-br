---
title: 'Como: Escrever consultas no XML em namespaces (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 1ded47ced44bebfda92b96f4dc908f1c1b2bbf6b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253191"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="d33d1-102">Como: Escrever consultas no XML em namespaces (C#)</span><span class="sxs-lookup"><span data-stu-id="d33d1-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="d33d1-103">Para escrever uma consulta em XML que está em um namespace, você deve usar os objetos <xref:System.Xml.Linq.XName> que têm o namespace correto.</span><span class="sxs-lookup"><span data-stu-id="d33d1-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="d33d1-104">Para C#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, em seguida, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.</span><span class="sxs-lookup"><span data-stu-id="d33d1-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="d33d1-105">O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d33d1-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="d33d1-106">O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="d33d1-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d33d1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d33d1-107">Example</span></span>  
 <span data-ttu-id="d33d1-108">O exemplo a seguir cria uma árvore XML que está em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d33d1-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="d33d1-109">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="d33d1-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="d33d1-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d33d1-110">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="d33d1-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d33d1-111">Example</span></span>  
 <span data-ttu-id="d33d1-112">No C#, você escreve consultas da mesma forma independentemente se estiver escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d33d1-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="d33d1-113">O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="d33d1-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="d33d1-114">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="d33d1-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="d33d1-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d33d1-115">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="d33d1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d33d1-116">See also</span></span>

- [<span data-ttu-id="d33d1-117">Visão geral sobre namespaces (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d33d1-117">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
