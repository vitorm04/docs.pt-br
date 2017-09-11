---
title: Mantendo pares nome-valor (C#)
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
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9515411123ad800df4e800d698921b76f6590286
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="c35a8-102">Mantendo pares nome-valor (C#)</span><span class="sxs-lookup"><span data-stu-id="c35a8-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="c35a8-103">Muitos aplicativos devem manter informações que são melhor armazenadas como pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="c35a8-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="c35a8-104">Essas informações podem ser informações de configuração ou configurações globais.</span><span class="sxs-lookup"><span data-stu-id="c35a8-104">This information might be configuration information or global settings.</span></span> <span data-ttu-id="c35a8-105">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] contém alguns métodos que facilitam o trabalho de manter um conjunto de pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="c35a8-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="c35a8-106">É possível manter informações como atributos ou como um conjunto de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="c35a8-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="c35a8-107">Uma das diferenças entre manter as informações como atributos ou como elementos filho é que os atributos possuem a restrição de que pode existir apenas um atributo com um nome específico para um elemento.</span><span class="sxs-lookup"><span data-stu-id="c35a8-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="c35a8-108">Essa limitação não se aplica aos elementos filho.</span><span class="sxs-lookup"><span data-stu-id="c35a8-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="c35a8-109">SetAttributeValue e SetElementValue</span><span class="sxs-lookup"><span data-stu-id="c35a8-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="c35a8-110">Os dois métodos que facilitam o trabalho de manter pares de valor/nome são <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> e <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="c35a8-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="c35a8-111">Esses dois métodos possuem semântica semelhante.</span><span class="sxs-lookup"><span data-stu-id="c35a8-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="c35a8-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> pode adicionar, modificar ou remover atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="c35a8-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="c35a8-113">Ao designar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com o nome de um atributo inexistente, o método cria um novo atributo e o adiciona ao elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="c35a8-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="c35a8-114">Ao designar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com o nome de um atributo existente e algum conteúdo especificado, o conteúdo do atributo é substituído pelo conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="c35a8-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="c35a8-115">Ao designar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com o nome de um atributo existente e especificar nulo em relação ao conteúdo, o atributo é removido de seu pai.</span><span class="sxs-lookup"><span data-stu-id="c35a8-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="c35a8-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> pode adicionar, modificar, ou remover elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="c35a8-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="c35a8-117">Ao designar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com o nome de um elemento filho que não existe, o método cria um novo elemento e o adiciona ao elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="c35a8-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="c35a8-118">Ao designar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com o nome de um elemento existente e algum conteúdo especificado, o conteúdo do elemento é substituído pelo conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="c35a8-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="c35a8-119">Ao designar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com o nome de um elemento existente e especificar nulo em relação ao conteúdo, o elemento é removido de seu pai.</span><span class="sxs-lookup"><span data-stu-id="c35a8-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c35a8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c35a8-120">Example</span></span>  
 <span data-ttu-id="c35a8-121">O exemplo a seguir cria um elemento sem atributos.</span><span class="sxs-lookup"><span data-stu-id="c35a8-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="c35a8-122">Usa o método <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> para criar e manter uma lista de pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="c35a8-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="c35a8-123">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c35a8-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="c35a8-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c35a8-124">Example</span></span>  
 <span data-ttu-id="c35a8-125">O exemplo a seguir cria um elemento sem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="c35a8-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="c35a8-126">Usa o método <xref:System.Xml.Linq.XElement.SetElementValue%2A> para criar e manter uma lista de pares de valor/nome.</span><span class="sxs-lookup"><span data-stu-id="c35a8-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="c35a8-127">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c35a8-127">This example produces the following output:</span></span>  
  
```xml  
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
  
## <a name="see-also"></a><span data-ttu-id="c35a8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c35a8-128">See Also</span></span>  
 <span data-ttu-id="c35a8-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="c35a8-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span></span>   
 <span data-ttu-id="c35a8-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="c35a8-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span></span>   
 [<span data-ttu-id="c35a8-131">Modificando árvores XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c35a8-131">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

