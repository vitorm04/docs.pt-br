---
title: "Visão geral da classe de XAttribute (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
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
ms.openlocfilehash: 741e73987a9339a320114d74187c0056c7150924
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="9d0b9-102">Visão geral da classe de XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0b9-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="9d0b9-103">Os atributos são pares nome/valor que são associados a um elemento.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="9d0b9-104">O <xref:System.Xml.Linq.XAttribute>classe representa atributos XML.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9d0b9-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9d0b9-105">Overview</span></span>  
 <span data-ttu-id="9d0b9-106">Trabalhar com atributos em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é semelhante a trabalhar com elementos.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-106">Working with attributes in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is similar to working with elements.</span></span> <span data-ttu-id="9d0b9-107">Os construtores são semelhantes.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-107">Their constructors are similar.</span></span> <span data-ttu-id="9d0b9-108">Os métodos que você usa para recuperar coleções deless são semelhantes.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="9d0b9-109">A [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão de consulta para uma coleção de atributos parece muito semelhante a um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão para uma coleção de elementos de consulta.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-109">A [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="9d0b9-110">A ordem em que os atributos foram adicionados a um elemento é preservada.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="9d0b9-111">Isto é, quando você itera através de atributos, você ver na mesma ordem que foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="9d0b9-112">O construtor de XAttribute</span><span class="sxs-lookup"><span data-stu-id="9d0b9-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="9d0b9-113">O seguinte construtor da <xref:System.Xml.Linq.XAttribute>classe é aquele que você usará mais comumente:</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="9d0b9-114">Construtor</span><span class="sxs-lookup"><span data-stu-id="9d0b9-114">Constructor</span></span>|<span data-ttu-id="9d0b9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d0b9-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="9d0b9-116">Cria um <xref:System.Xml.Linq.XAttribute>objeto.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="9d0b9-117">O argumento de `name` especifica o nome do atributo; `content` especifica o conteúdo de atributo.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="9d0b9-118">Criando um elemento com um atributo</span><span class="sxs-lookup"><span data-stu-id="9d0b9-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="9d0b9-119">O código a seguir mostra um elemento que contém um atributo usando literais XML no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9d0b9-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="9d0b9-120">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9d0b9-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="9d0b9-121">Compilação funcional de atributos</span><span class="sxs-lookup"><span data-stu-id="9d0b9-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="9d0b9-122">Você pode construir <xref:System.Xml.Linq.XAttribute>objetos em linha com a construção de <xref:System.Xml.Linq.XElement>objetos, da seguinte maneira:</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="9d0b9-123">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9d0b9-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="9d0b9-124">Os atributos não são nós</span><span class="sxs-lookup"><span data-stu-id="9d0b9-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="9d0b9-125">Há algumas diferenças entre atributos e elementos.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="9d0b9-126"><xref:System.Xml.Linq.XAttribute>objetos não são nós na árvore XML.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="9d0b9-127">São pares nome/valor associados com um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="9d0b9-128">Em contraste com Document Object Model (DOM), este reflete mais apertadamente a estrutura XML.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="9d0b9-129">Embora <xref:System.Xml.Linq.XAttribute>objetos não são realmente nós na árvore de XML, trabalhar com <xref:System.Xml.Linq.XAttribute>objetos é muito semelhante a trabalhar com <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9d0b9-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="9d0b9-130">Essa distinção importante é primeiro somente para os desenvolvedores que estão escrevendo código que funciona com as árvores XML no nível do nó.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="9d0b9-131">Muitos desenvolvedores não serão preocupados com essa distinção.</span><span class="sxs-lookup"><span data-stu-id="9d0b9-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0b9-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d0b9-132">See Also</span></span>  
 [<span data-ttu-id="9d0b9-133">LINQ para visão geral da programação XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0b9-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
