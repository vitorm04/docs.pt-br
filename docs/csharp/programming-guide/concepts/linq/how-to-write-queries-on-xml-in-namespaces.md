---
title: Como escrever consultas em XML em namespaces (C#)
description: Saiba como escrever consultas em XML em namespaces. Para essas consultas, você deve usar os objetos XName que têm o namespace correto.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303173"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="d5701-104">Como escrever consultas em XML em namespaces (C#)</span><span class="sxs-lookup"><span data-stu-id="d5701-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="d5701-105">Para escrever uma consulta em XML que está em um namespace, você deve usar os objetos <xref:System.Xml.Linq.XName> que têm o namespace correto.</span><span class="sxs-lookup"><span data-stu-id="d5701-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="d5701-106">Para C#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, em seguida, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.</span><span class="sxs-lookup"><span data-stu-id="d5701-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="d5701-107">O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d5701-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="d5701-108">O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="d5701-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5701-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5701-109">Example</span></span>  
 <span data-ttu-id="d5701-110">O exemplo a seguir cria uma árvore XML que está em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d5701-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="d5701-111">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="d5701-111">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="d5701-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5701-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="d5701-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5701-113">Example</span></span>  
 <span data-ttu-id="d5701-114">No C#, você escreve consultas da mesma forma independentemente se estiver escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="d5701-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="d5701-115">O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="d5701-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="d5701-116">Ele então recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="d5701-116">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="d5701-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5701-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5701-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5701-118">See also</span></span>

- [<span data-ttu-id="d5701-119">Visão geral sobre namespaces (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5701-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
