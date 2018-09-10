---
title: Visão geral da classe XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: cc571eac2af824d02ce34b018cfd51fb186f8bf6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527478"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="68622-102">Visão geral da classe XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="68622-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="68622-103">A classe <xref:System.Xml.Linq.XElement> é uma das classes fundamentais no [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68622-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="68622-104">Representa um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="68622-104">It represents an XML element.</span></span> <span data-ttu-id="68622-105">Você pode usar essa classe para criar elementos; alterar o conteúdo do elemento; adicionar, alterar ou excluir elementos filho; adicionar atributos a um elemento; ou serializar o conteúdo de um elemento no formulário de texto.</span><span class="sxs-lookup"><span data-stu-id="68622-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="68622-106">Você também pode interoperar com outras classes no <xref:System.Xml?displayProperty=nameWithType>, como <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> e <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="68622-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="68622-107">Funcionalidade de XElement</span><span class="sxs-lookup"><span data-stu-id="68622-107">XElement Functionality</span></span>  
 <span data-ttu-id="68622-108">Este tópico descreve a funcionalidade fornecida pela classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="68622-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="68622-109">Construindo árvores XML</span><span class="sxs-lookup"><span data-stu-id="68622-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="68622-110">Você pode construir árvores XML em uma variedade de maneiras, incluindo:</span><span class="sxs-lookup"><span data-stu-id="68622-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="68622-111">Você pode construir uma árvore XML em código.</span><span class="sxs-lookup"><span data-stu-id="68622-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="68622-112">Para obter mais informações, consulte [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="68622-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="68622-113">Você pode analisar XML de várias fontes, incluindo <xref:System.IO.TextReader>, arquivos de texto ou um endereço Web (URL).</span><span class="sxs-lookup"><span data-stu-id="68622-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="68622-114">Para obter mais informações, consulte [Analisando XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="68622-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="68622-115">Você pode usar um <xref:System.Xml.XmlReader> para popular a árvore.</span><span class="sxs-lookup"><span data-stu-id="68622-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="68622-116">Para obter mais informações, consulte <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="68622-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="68622-117">Se você tiver um módulo que possa gravar conteúdo em um <xref:System.Xml.XmlWriter>, poderá usar o método <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um gravador, passar o gravador para o módulo e usar o conteúdo que está gravado no <xref:System.Xml.XmlWriter> para popular a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="68622-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="68622-118">No entanto, a maneira mais comum de criar uma árvore XML é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="68622-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="68622-119">Outra técnica muito comum para criar uma árvore XML envolve o uso dos resultados de uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para popular uma árvore XML, conforme mostrado no exemplo o seguir:</span><span class="sxs-lookup"><span data-stu-id="68622-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="68622-120">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="68622-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="68622-121">Serializando árvores XML</span><span class="sxs-lookup"><span data-stu-id="68622-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="68622-122">Você pode serializar a árvore XML para um <xref:System.IO.File>, um <xref:System.IO.TextWriter> ou um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="68622-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="68622-123">Para obter mais informações, consulte [Serializando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="68622-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="68622-124">Recuperando dados XML por meio de métodos de eixo</span><span class="sxs-lookup"><span data-stu-id="68622-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="68622-125">Você pode usar métodos de eixo para recuperar atributos, elementos filho, elementos descendentes e elementos ancestrais.</span><span class="sxs-lookup"><span data-stu-id="68622-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="68622-126">As consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operam em métodos de eixo e fornecem várias maneiras flexíveis e avançadas de navegar por uma árvore XML e de processá-la.</span><span class="sxs-lookup"><span data-stu-id="68622-126">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="68622-127">Para obter mais informações, consulte [Eixos LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="68622-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="68622-128">Consultando árvores XML</span><span class="sxs-lookup"><span data-stu-id="68622-128">Querying XML Trees</span></span>  
 <span data-ttu-id="68622-129">Você pode escrever consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] que extraem dados de uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="68622-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="68622-130">Para obter mais informações, consulte [Consultando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="68622-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="68622-131">Modificando árvores XML</span><span class="sxs-lookup"><span data-stu-id="68622-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="68622-132">Você pode modificar um elemento de várias maneiras, incluindo alterar seu conteúdo ou atributos.</span><span class="sxs-lookup"><span data-stu-id="68622-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="68622-133">Você também pode remover um elemento de seu pai.</span><span class="sxs-lookup"><span data-stu-id="68622-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="68622-134">Para obter mais informações, consulte [Modificando árvores XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="68622-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68622-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68622-135">See Also</span></span>

- [<span data-ttu-id="68622-136">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="68622-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
