---
title: Mantendo pares de nome-valor (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 30e40c73430f385815b7a08a2507343db0fafd4f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="37ccd-102">Mantendo pares de nome/valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37ccd-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="37ccd-103">Muitos aplicativos devem manter informações que são melhor armazenadas como pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="37ccd-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="37ccd-104">Essas informações podem ser informações de configuração ou configurações globais.</span><span class="sxs-lookup"><span data-stu-id="37ccd-104">This information might be configuration information or global settings.</span></span> <span data-ttu-id="37ccd-105">O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] contém alguns métodos que facilitam o trabalho de manter um conjunto de pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="37ccd-105">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="37ccd-106">É possível manter informações como atributos ou como um conjunto de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="37ccd-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="37ccd-107">Uma das diferenças entre manter as informações como atributos ou como elementos filho é que os atributos possuem a restrição de que pode existir apenas um atributo com um nome específico para um elemento.</span><span class="sxs-lookup"><span data-stu-id="37ccd-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="37ccd-108">Essa limitação não se aplica aos elementos filho.</span><span class="sxs-lookup"><span data-stu-id="37ccd-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="37ccd-109">SetAttributeValue e SetElementValue</span><span class="sxs-lookup"><span data-stu-id="37ccd-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="37ccd-110">Os dois métodos que facilitam a manutenção de nome/valor pares são <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>e <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</xref:System.Xml.Linq.XElement.SetElementValue%2A> </xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="37ccd-111">Esses dois métodos possuem semântica semelhante.</span><span class="sxs-lookup"><span data-stu-id="37ccd-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="37ccd-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>pode adicionar, modificar ou remover atributos de um elemento.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="37ccd-113">Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um atributo que não existe, o método cria um novo atributo e o adiciona ao elemento especificado.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="37ccd-114">Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um atributo existente e algum especificado conteúdo, o conteúdo do atributo é substituído pelo conteúdo especificado.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="37ccd-115">Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um objeto existente do atributo e especifique null para o conteúdo, o atributo é removido de seu pai.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="37ccd-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>pode adicionar, modificar ou remover elementos filho de um elemento.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="37ccd-117">Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com o nome de um elemento filho que não existe, o método cria um novo elemento e o adiciona ao elemento especificado.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="37ccd-118">Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com um nome de um elemento existente e algum especificado conteúdo, o conteúdo do elemento é substituído pelo conteúdo especificado.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="37ccd-119">Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com o nome de um elemento existente e especificar nulo para o conteúdo, o elemento é removido de seu pai.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ccd-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37ccd-120">Example</span></span>  
 <span data-ttu-id="37ccd-121">O exemplo a seguir cria um elemento sem atributos.</span><span class="sxs-lookup"><span data-stu-id="37ccd-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="37ccd-122">Ele usa o <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>método para criar e manter uma lista de pares nome/valor.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="37ccd-123">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="37ccd-123">This example produces the following output:</span></span>  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="37ccd-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37ccd-124">Example</span></span>  
 <span data-ttu-id="37ccd-125">O exemplo a seguir cria um elemento sem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="37ccd-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="37ccd-126">Ele usa o <xref:System.Xml.Linq.XElement.SetElementValue%2A>método para criar e manter uma lista de pares nome/valor.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
  
```  
  
 <span data-ttu-id="37ccd-127">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="37ccd-127">This example produces the following output:</span></span>  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37ccd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37ccd-128">See Also</span></span>  
 <span data-ttu-id="37ccd-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span></span>   
 <span data-ttu-id="37ccd-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="37ccd-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span></span>   
<span data-ttu-id="37ccd-131"> [Modificando árvores XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="37ccd-131"> [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)</span></span>
