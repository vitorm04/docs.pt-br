---
title: Trabalhar com Namespaces globais (Visual Basic) (LINQ to XML) | Documentos do Microsoft
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
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
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
ms.openlocfilehash: 6d92bdf80fa5db0003dfc0c6af7f0e8f6c3b2334
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="0998f-102">Trabalhar com namespaces globais (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0998f-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="0998f-103">Um dos principais recursos dos literais XML no Visual Basic é a capacidade de declarar namespaces XML usando o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="0998f-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="0998f-104">Usando esse recurso, você pode declarar um namespace XML que usa um prefixo, ou você pode declarar um namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="0998f-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="0998f-105">Esse recurso é útil em duas situações.</span><span class="sxs-lookup"><span data-stu-id="0998f-105">This capability is useful in two situations.</span></span> <span data-ttu-id="0998f-106">Primeiro, namespaces declaradas em literais XML não transferem em expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="0998f-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="0998f-107">Declarar namespaces globais reduz a quantidade de trabalho que você tem que fazer para usar expressões inseridas com namespaces.</span><span class="sxs-lookup"><span data-stu-id="0998f-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="0998f-108">Segundo, você deve declarar namespaces globais para usar namespaces com propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="0998f-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="0998f-109">Você pode declarar namespaces globais no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="0998f-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="0998f-110">Você também pode declarar namespaces globais em nível de módulo, que substitui namespaces globais no nível de projeto.</span><span class="sxs-lookup"><span data-stu-id="0998f-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="0998f-111">Finalmente, você pode substituir namespaces globais em um literal XML.</span><span class="sxs-lookup"><span data-stu-id="0998f-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="0998f-112">Ao usar as literal XML ou propriedades XML que estão em namespaces globais - declaradas, você pode ver o nome do literal XML ou propriedades focalizando sobre eles em Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0998f-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="0998f-113">Você verá o nome expandido em uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0998f-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="0998f-114">Você pode obter um <xref:System.Xml.Linq.XNamespace>objeto corresponde a um namespace global usando o `GetXmlNamespace` método.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="0998f-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="0998f-115">Exemplos de namespaces globais</span><span class="sxs-lookup"><span data-stu-id="0998f-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="0998f-116">O exemplo a seguir declara um namespace global padrão usando o `Imports` instrução e, em seguida, usa um literal XML para inicializar um <xref:System.Xml.Linq.XElement>objeto nesse namespace:</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="0998f-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0998f-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="0998f-118">O exemplo a seguir declara um namespace global com um prefixo em seguida, usa uma literal XML para inicializar um elemento:</span><span class="sxs-lookup"><span data-stu-id="0998f-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0998f-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="0998f-120">Namespaces globais e expressões inseridas</span><span class="sxs-lookup"><span data-stu-id="0998f-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="0998f-121">Namespaces que são declaradas em literais XML não transferem em expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="0998f-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="0998f-122">O exemplo a seguir declara um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="0998f-122">The following example declares a default namespace.</span></span> <span data-ttu-id="0998f-123">Usar uma expressão inserida para o elemento de `Child` .</span><span class="sxs-lookup"><span data-stu-id="0998f-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="0998f-124">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="0998f-125">Como você pode ver, XML resultante inclui uma declaração de namespace padrão para que o elemento de `Child` está em qualquer namespace.</span><span class="sxs-lookup"><span data-stu-id="0998f-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="0998f-126">Você pode declarar novamente o namespace na expressão inserida, como segue:</span><span class="sxs-lookup"><span data-stu-id="0998f-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="0998f-127">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="0998f-128">No entanto, isso é mais incômodo usar que o namespace global padrão, que é uma abordagem melhor.</span><span class="sxs-lookup"><span data-stu-id="0998f-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="0998f-129">Com o namespace global padrão, você pode usar literais XML sem declarar namespaces.</span><span class="sxs-lookup"><span data-stu-id="0998f-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="0998f-130">XML resultante será no namespace padrão globais - declarada.</span><span class="sxs-lookup"><span data-stu-id="0998f-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0998f-131">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="0998f-132">Usando namespaces XML com propriedades</span><span class="sxs-lookup"><span data-stu-id="0998f-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="0998f-133">Se você estiver trabalhando com uma árvore XML que está em um namespace, e você usa propriedades XML, então você deve usar um namespace global de modo que as propriedades XML também estão no namespace correta.</span><span class="sxs-lookup"><span data-stu-id="0998f-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="0998f-134">O exemplo a seguir declara uma árvore XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="0998f-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="0998f-135">Imprime na contagem de elementos de `Child` .</span><span class="sxs-lookup"><span data-stu-id="0998f-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="0998f-136">Este exemplo indica que não há nenhum elemento de `Child` .</span><span class="sxs-lookup"><span data-stu-id="0998f-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="0998f-137">Gerencia a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0998f-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="0998f-138">Se, no entanto, você declarar um namespace global padrão, então a literal XML e a propriedade XML estão no namespace global padrão:</span><span class="sxs-lookup"><span data-stu-id="0998f-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0998f-139">Este exemplo indica que há um elemento de `Child` .</span><span class="sxs-lookup"><span data-stu-id="0998f-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="0998f-140">Gerencia a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0998f-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="0998f-141">Se você declarar um namespace global que tenha um prefixo, você pode usar o prefixo para literais XML e propriedades XML:</span><span class="sxs-lookup"><span data-stu-id="0998f-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="0998f-142">XNamespace e namespaces globais</span><span class="sxs-lookup"><span data-stu-id="0998f-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="0998f-143">Você pode obter um <xref:System.Xml.Linq.XNamespace>objeto usando o `GetXmlNamespace` método:</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="0998f-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0998f-144">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0998f-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="0998f-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0998f-145">See Also</span></span>  
 [<span data-ttu-id="0998f-146">Trabalhando com Namespaces XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0998f-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
