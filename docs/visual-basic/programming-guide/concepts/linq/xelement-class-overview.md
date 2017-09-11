---
title: "Visão geral da classe de XElement (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
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
ms.openlocfilehash: 78a72effa021408943b9248546106c6fd655ac0b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="b6642-102">Visão geral da classe de XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6642-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b6642-103">O <xref:System.Xml.Linq.XElement>classe é uma das classes fundamentais no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6642-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="b6642-104">Representa um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="b6642-104">It represents an XML element.</span></span> <span data-ttu-id="b6642-105">Você pode usar essa classe para criar elementos; alterar o conteúdo do elemento; adicionar, alterar ou excluir elementos filho; adicionar atributos a um elemento; ou serializar o conteúdo de um elemento no formulário de texto.</span><span class="sxs-lookup"><span data-stu-id="b6642-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="b6642-106">Você também pode interoperar com outras classes no <xref:System.Xml?displayProperty=fullName>, como <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>e <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b6642-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=fullName>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="b6642-107">Funcionalidade de XElement</span><span class="sxs-lookup"><span data-stu-id="b6642-107">XElement Functionality</span></span>  
 <span data-ttu-id="b6642-108">Este tópico descreve a funcionalidade fornecida pela <xref:System.Xml.Linq.XElement>classe.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6642-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="b6642-109">Construindo árvores XML</span><span class="sxs-lookup"><span data-stu-id="b6642-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="b6642-110">Você pode construir árvores XML em uma variedade de maneiras, incluindo:</span><span class="sxs-lookup"><span data-stu-id="b6642-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="b6642-111">Você pode construir uma árvore XML em código.</span><span class="sxs-lookup"><span data-stu-id="b6642-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="b6642-112">Para obter mais informações, consulte [criar árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="b6642-113">Você pode analisar o XML de várias fontes, incluindo um <xref:System.IO.TextReader>, arquivos de texto ou um endereço Web (URL).</xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="b6642-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="b6642-114">Para obter mais informações, consulte [a análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="b6642-115">Você pode usar um <xref:System.Xml.XmlReader>para popular a árvore.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="b6642-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="b6642-116">Para obter mais informações, consulte <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="b6642-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="b6642-117">Se você tiver um módulo que possa gravar conteúdo em um <xref:System.Xml.XmlWriter>, você pode usar o <xref:System.Xml.Linq.XContainer.CreateWriter%2A>método para criar um gravador, passar o gravador para o módulo e, em seguida, usar o conteúdo gravado para o <xref:System.Xml.XmlWriter>para popular a árvore XML.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> </xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="b6642-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="b6642-118">No entanto, a maneira mais comum de criar uma árvore XML é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6642-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="b6642-119">Outra técnica muito comum para a criação de uma árvore XML envolve usando os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para preencher uma árvore XML, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6642-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="b6642-120">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b6642-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="b6642-121">Serializando árvores XML</span><span class="sxs-lookup"><span data-stu-id="b6642-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="b6642-122">Você pode serializar a árvore XML para um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="b6642-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b6642-123">Para obter mais informações, consulte [serializando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="b6642-124">Recuperando dados XML por meio de métodos de eixo</span><span class="sxs-lookup"><span data-stu-id="b6642-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="b6642-125">Você pode usar métodos de eixo para recuperar atributos, elementos filho, elementos descendentes e elementos ancestrais.</span><span class="sxs-lookup"><span data-stu-id="b6642-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="b6642-126">As consultas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] operam em métodos de eixo e fornecem várias maneiras flexíveis e avançadas de navegar por uma árvore XML e de processá-la.</span><span class="sxs-lookup"><span data-stu-id="b6642-126">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="b6642-127">Para obter mais informações, consulte [eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="b6642-128">Consultando árvores XML</span><span class="sxs-lookup"><span data-stu-id="b6642-128">Querying XML Trees</span></span>  
 <span data-ttu-id="b6642-129">Você pode escrever [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas que extraem dados de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="b6642-129">You can write [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="b6642-130">Para obter mais informações, consulte [consultando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="b6642-131">Modificando árvores XML</span><span class="sxs-lookup"><span data-stu-id="b6642-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="b6642-132">Você pode modificar um elemento de várias maneiras, incluindo alterar seu conteúdo ou atributos.</span><span class="sxs-lookup"><span data-stu-id="b6642-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="b6642-133">Você também pode remover um elemento de seu pai.</span><span class="sxs-lookup"><span data-stu-id="b6642-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="b6642-134">Para obter mais informações, consulte [modificando árvores XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6642-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6642-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6642-135">See Also</span></span>  
 [<span data-ttu-id="b6642-136">LINQ para visão geral da programação XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6642-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
