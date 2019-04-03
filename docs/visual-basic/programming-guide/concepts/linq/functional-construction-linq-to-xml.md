---
title: Construção funcional (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816545"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="02c0a-102">Construção funcional (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c0a-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="02c0a-103">fornece uma maneira eficiente de criar elementos XML chamada *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="02c0a-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="02c0a-104">Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="02c0a-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="02c0a-105">Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] que permitem a construção funcional:</span><span class="sxs-lookup"><span data-stu-id="02c0a-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="02c0a-106">O construtor <xref:System.Xml.Linq.XElement> utiliza vários tipos de argumentos para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="02c0a-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="02c0a-107">Por exemplo, você pode passar outro objeto <xref:System.Xml.Linq.XElement>, que se torna um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="02c0a-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="02c0a-108">Você pode passar um objeto <xref:System.Xml.Linq.XAttribute>, que se torna um atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="02c0a-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="02c0a-109">Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.</span><span class="sxs-lookup"><span data-stu-id="02c0a-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="02c0a-110">O construtor <xref:System.Xml.Linq.XElement> utiliza uma matriz de `params` do tipo <xref:System.Object>, para que você possa passar qualquer número de objetos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="02c0a-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="02c0a-111">Isso permite que você crie um elemento que tem o conteúdo complexo.</span><span class="sxs-lookup"><span data-stu-id="02c0a-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="02c0a-112">Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados.</span><span class="sxs-lookup"><span data-stu-id="02c0a-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="02c0a-113">Se a coleção contiver objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente.</span><span class="sxs-lookup"><span data-stu-id="02c0a-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="02c0a-114">Isso é importante porque permite que você passe os resultados de uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para o construtor.</span><span class="sxs-lookup"><span data-stu-id="02c0a-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="02c0a-115">A seguir está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="02c0a-115">The following is an example:</span></span>  
  
 <span data-ttu-id="02c0a-116">Esses recursos permitem que você escreva código usando literais XML para criar uma árvore XML e também para escrever um código que usa os resultados de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas quando você cria uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="02c0a-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="02c0a-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="02c0a-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02c0a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c0a-118">See also</span></span>

- [<span data-ttu-id="02c0a-119">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c0a-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
