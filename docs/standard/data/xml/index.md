---
title: Documentos e dados XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 22a2eb72dc06a644171c143a61698e661d2c66c6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="1d837-102">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="1d837-102">XML Documents and Data</span></span>
<span data-ttu-id="1d837-103">O .NET Framework fornece um conjunto de classes abrangente e integrado que permite que você crie aplicativos com reconhecimento de XML facilmente.</span><span class="sxs-lookup"><span data-stu-id="1d837-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="1d837-104">As classes nos namespaces a seguir suportam a análise e gravação de XML, edição de dados XML na memória, validação de dados e transformação de XSLT.</span><span class="sxs-lookup"><span data-stu-id="1d837-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="1d837-105">Para obter uma lista completa, consulte a página da Web [Namespaces System.Xml](http://msdn.microsoft.com/library/gg145036.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d837-105">For a full list, see the [System.Xml Namespaces](http://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="1d837-106">As classes nesses namespaces suportam recomendações World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="1d837-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="1d837-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1d837-107">For example:</span></span>  
  
-   <span data-ttu-id="1d837-108">A classe <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementa as recomendações do [DOM (Modelo de Objeto do Documento) Core do W3C nível 1](http://www.w3.org/TR/REC-DOM-Level-1/) e do [DOM Core nível 2](http://www.w3.org/TR/DOM-Level-2-Core/).</span><span class="sxs-lookup"><span data-stu-id="1d837-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="1d837-109">As classes <xref:System.Xml.XmlReader?displayProperty=nameWithType> e <xref:System.Xml.XmlWriter?displayProperty=nameWithType> dão suporte para as recomendações [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) e [Namespaces em XML](http://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="1d837-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="1d837-110">Os esquemas na classe <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> dão suporte para as recomendações do [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) (Esquema XML do W3C Parte 1: estruturas) e do [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) (Esquema XML Parte 2: tipos de dados).</span><span class="sxs-lookup"><span data-stu-id="1d837-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="1d837-111">As classes no namespace <xref:System.Xml.Xsl?displayProperty=nameWithType> dão suporte para as transformações XSLT que estão em conformidade com a recomendação [W3C XSLT 1.0](http://www.w3.org/TR/xslt).</span><span class="sxs-lookup"><span data-stu-id="1d837-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="1d837-112">As classes XML do .NET Framework fornecem esses benefícios:</span><span class="sxs-lookup"><span data-stu-id="1d837-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="1d837-113">**Produtividade.**</span><span class="sxs-lookup"><span data-stu-id="1d837-113">**Productivity.**</span></span> <span data-ttu-id="1d837-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) facilita a programação com XML e fornece uma experiência de consulta que é semelhante a SQL.</span><span class="sxs-lookup"><span data-stu-id="1d837-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="1d837-115">**Extensibilidade.**</span><span class="sxs-lookup"><span data-stu-id="1d837-115">**Extensibility.**</span></span> <span data-ttu-id="1d837-116">As classes XML no .NET Framework são extensíveis pelo uso de classes base abstratas e métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="1d837-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="1d837-117">Por exemplo, você pode criar uma classe derivada da classe de <xref:System.Xml.XmlUrlResolver> que armazena o fluxo de cache no disco local.</span><span class="sxs-lookup"><span data-stu-id="1d837-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="1d837-118">**Arquitetura conectável.**</span><span class="sxs-lookup"><span data-stu-id="1d837-118">**Pluggable architecture.**</span></span> <span data-ttu-id="1d837-119">O .NET Framework fornece uma arquitetura na qual os componentes podem se utilizar uns aos outros e os dados podem ser transmitidos entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="1d837-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="1d837-120">Por exemplo, um armazenamento de dados, tal como um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>, pode ser transformado com a classe <xref:System.Xml.Xsl.XslCompiledTransform> e a saída pode então ser transmitida para outro armazenamento ou retornados como um fluxo de um serviço da web.</span><span class="sxs-lookup"><span data-stu-id="1d837-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="1d837-121">**Desempenho.**</span><span class="sxs-lookup"><span data-stu-id="1d837-121">**Performance.**</span></span> <span data-ttu-id="1d837-122">Para melhorar o desempenho do aplicativo, algumas das classes XML do .NET Framework dão suporte a um modelo baseado em streaming com as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="1d837-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="1d837-123">Armazenamento em cache mínimo para somente encaminhamento, análise de recepção modelo (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="1d837-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="1d837-124">Validação somente de encaminhamento (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="1d837-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="1d837-125">Navegação do cursor que minimiza a criação do nó com um único nó virtual no entanto fornece acesso aleatório ao documento (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="1d837-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="1d837-126">Para obter um melhor desempenho sempre que o processamento de XSLT for necessário, você pode usar a classe <xref:System.Xml.XPath.XPathDocument>, que é um repositório otimizado, somente de leitura para consultas do XPath projetado para trabalhar com eficiência com a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1d837-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="1d837-127">**Integração com o ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="1d837-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="1d837-128">As classes XML e o [ADO.NET](../../../../docs/framework/data/adonet/index.md) são bem integrados para reunir dados relacionais e XML.</span><span class="sxs-lookup"><span data-stu-id="1d837-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="1d837-129">A classe de <xref:System.Data.DataSet> é um cache de memória dos dados recuperados de uma base de dados.</span><span class="sxs-lookup"><span data-stu-id="1d837-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="1d837-130">A classe <xref:System.Data.DataSet> tem a capacidade de ler e escrever XML usando as classes de <xref:System.Xml.XmlReader> e de <xref:System.Xml.XmlWriter> , para manter sua estrutura de esquema relacional como esquemas XML (XSD), e para interpretar a estrutura do esquema de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="1d837-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d837-131">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1d837-131">In This Section</span></span>  
 <span data-ttu-id="1d837-132">[XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md) (Opções de processamento de XML)</span><span class="sxs-lookup"><span data-stu-id="1d837-132">[XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md)</span></span>  
 <span data-ttu-id="1d837-133">Discute opções para processar dados XML.</span><span class="sxs-lookup"><span data-stu-id="1d837-133">Discusses options for processing XML data.</span></span>  
  
 <span data-ttu-id="1d837-134">[Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) (Processamento de dados XML na memória)</span><span class="sxs-lookup"><span data-stu-id="1d837-134">[Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)</span></span>  
 <span data-ttu-id="1d837-135">Discute os três modelos para processar dados XML na memória.</span><span class="sxs-lookup"><span data-stu-id="1d837-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="1d837-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), a classe <xref:System.Xml.XmlDocument> (com base no Modelo de Objeto do Documento do W3C) e a classe <xref:System.Xml.XPath.XPathDocument> (com base no modelo de dados do XPath).</span><span class="sxs-lookup"><span data-stu-id="1d837-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="1d837-137">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="1d837-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="1d837-138">Descreve como usar o processador XSLT.</span><span class="sxs-lookup"><span data-stu-id="1d837-138">Describes how to use the XSLT processor.</span></span>  
  
 <span data-ttu-id="1d837-139">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]</span><span class="sxs-lookup"><span data-stu-id="1d837-139">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>  
 <span data-ttu-id="1d837-140">Descreve as classes usadas para criar e manipular esquemas XML (XSD), fornecendo uma classe <xref:System.Xml.Schema.XmlSchema> para carregar e editar um esquema.</span><span class="sxs-lookup"><span data-stu-id="1d837-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 <span data-ttu-id="1d837-141">[XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md) (Integração XML com os dados relacionais e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1d837-141">[XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span></span>  
 <span data-ttu-id="1d837-142">Descreve como o .NET Framework habilita o acesso síncrono, em tempo real, às representações de dados relacionais e hierárquicas através dos objetos <xref:System.Data.DataSet> e <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="1d837-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 <span data-ttu-id="1d837-143">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md) (Gerenciando namespaces em um documento XML)</span><span class="sxs-lookup"><span data-stu-id="1d837-143">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span></span>  
 <span data-ttu-id="1d837-144">Descreve como a classe <xref:System.Xml.XmlNamespaceManager> classe é usada para armazenar e manter as informações do namespace.</span><span class="sxs-lookup"><span data-stu-id="1d837-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 <span data-ttu-id="1d837-145">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)</span><span class="sxs-lookup"><span data-stu-id="1d837-145">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>  
 <span data-ttu-id="1d837-146">Descreve como mapa de tipos de dados XML para tipos de CLR, como converter tipos de dados XML e outros recursos de suporte de tipo nas classes <xref:System.Xml>.</span><span class="sxs-lookup"><span data-stu-id="1d837-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d837-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1d837-147">Related Sections</span></span>  
 [<span data-ttu-id="1d837-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d837-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="1d837-149">Fornece informações sobre como acessar dados usando ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1d837-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="1d837-150">Segurança</span><span class="sxs-lookup"><span data-stu-id="1d837-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="1d837-151">Fornece uma visão geral do sistema de segurança do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d837-151">Provides an overview of the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="1d837-152">Centro de desenvolvimento de XML</span><span class="sxs-lookup"><span data-stu-id="1d837-152">XML Developer Center</span></span>](http://go.microsoft.com/fwlink/?linkid=42458)  
 <span data-ttu-id="1d837-153">Fornece informações técnicas, downloads, grupos de notícias e outros recursos adicionais para desenvolvedores do XML.</span><span class="sxs-lookup"><span data-stu-id="1d837-153">Provides additional technical information, downloads, newsgroups, and other resources for XML developers.</span></span>
