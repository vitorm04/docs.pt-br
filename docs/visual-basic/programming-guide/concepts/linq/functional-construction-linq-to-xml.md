---
title: "Construção funcional (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
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
ms.openlocfilehash: b88b67aca337b893f9f276c8e4a6589b6946069b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="01f5a-102">Construção funcional (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01f5a-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="01f5a-103">Fornece uma maneira eficiente de criar elementos XML chamados *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="01f5a-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="01f5a-104">Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="01f5a-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="01f5a-105">Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que permitem a construção funcional:</span><span class="sxs-lookup"><span data-stu-id="01f5a-105">There are several key features of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="01f5a-106">O <xref:System.Xml.Linq.XElement>construtor aceita vários tipos de argumentos para o conteúdo.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="01f5a-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="01f5a-107">Por exemplo, você pode passar outro <xref:System.Xml.Linq.XElement>objeto, que se torna um elemento filho.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="01f5a-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="01f5a-108">Você pode passar um <xref:System.Xml.Linq.XAttribute>objeto, que se torna um atributo do elemento.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="01f5a-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="01f5a-109">Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.</span><span class="sxs-lookup"><span data-stu-id="01f5a-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="01f5a-110">O <xref:System.Xml.Linq.XElement>construtor aceita um `params` matriz do tipo <xref:System.Object>, de modo que você pode passar qualquer número de objetos para o construtor.</xref:System.Object> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="01f5a-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="01f5a-111">Isso permite que você crie um elemento que tem o conteúdo complexo.</span><span class="sxs-lookup"><span data-stu-id="01f5a-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="01f5a-112">Se um objeto implementa <xref:System.Collections.Generic.IEnumerable%601>, a coleção do objeto é enumerada e todos os itens na coleção serão adicionados.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="01f5a-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="01f5a-113">Se a coleção contiver <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>objetos, cada item da coleção será adicionado separadamente.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="01f5a-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="01f5a-114">Isso é importante porque permite que você passe os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para o construtor.</span><span class="sxs-lookup"><span data-stu-id="01f5a-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="01f5a-115">A seguir está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="01f5a-115">The following is an example:</span></span>  
  
 <span data-ttu-id="01f5a-116">Esses recursos permitem que você escrever código usando literais XML para criar uma árvore XML e também para escrever um código que usa os resultados de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas quando você cria uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="01f5a-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="01f5a-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="01f5a-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01f5a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01f5a-118">See Also</span></span>  
 [<span data-ttu-id="01f5a-119">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01f5a-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
