---
title: "Transformações XSLT com a classe XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 619e37ab63735ea77d3afb0d94f284b2f310efc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="cc950-102">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="cc950-102">XSLT Transformations with the XslTransform Class</span></span>
> [!NOTE]
>  <span data-ttu-id="cc950-103">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc950-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="cc950-104">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="cc950-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cc950-105">Consulte [usando a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [migrar da classe de XslTransform o](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="cc950-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cc950-106">O objetivo do XSLT é transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura (por exemplo, para transformar XML em HTML para uso em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo).</span><span class="sxs-lookup"><span data-stu-id="cc950-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="cc950-107">Esse processo de transformação é especificado pela recomendação XSLT World Wide Web Consortium (W3C) versão 1.0 localizada em www.w3.org/TR/xslt.</span><span class="sxs-lookup"><span data-stu-id="cc950-107">This transformation process is specified by the World Wide Web Consortium (W3C) XSLT version 1.0 recommendation located at www.w3.org/TR/xslt.</span></span> <span data-ttu-id="cc950-108">No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], a classe <xref:System.Xml.Xsl.XslTransform>, localizada no namespace <xref:System.Xml.Xsl> é o processador XSLT que implementa a funcionalidade dessa especificação.</span><span class="sxs-lookup"><span data-stu-id="cc950-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="cc950-109">Há um pequeno número de recursos que não foram implementados de recomendação do W3C XSLT 1.0, listada em [saída de um XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="cc950-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="cc950-110">A figura a seguir mostra a arquitetura de transformação do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc950-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cc950-111">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="cc950-111">Overview</span></span>  
 <span data-ttu-id="cc950-112">![Arquitetura de transformação XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="cc950-112">![XSLT Transformation Architecture](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="cc950-113">Arquitetura de transformação</span><span class="sxs-lookup"><span data-stu-id="cc950-113">Transformation Architecture</span></span>  
  
 <span data-ttu-id="cc950-114">A recomendação XSLT usa a linguagem XPath para selecionar partes de um documento XML, onde XPath é uma linguagem de consulta usada para navegar em nós de uma árvore do documento.</span><span class="sxs-lookup"><span data-stu-id="cc950-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="cc950-115">Conforme mostrado no diagrama, a implementação de XPath do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é usada para selecionar partes de XML armazenadas em várias classes, como um <xref:System.Xml.XmlDocument>, um <xref:System.Xml.XmlDataDocument> e um <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc950-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="cc950-116">Um <xref:System.Xml.XPath.XPathDocument> é um repositório de dados XSLT otimizado e, quando usado com <xref:System.Xml.Xsl.XslTransform>, fornece transformações XSLT com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="cc950-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>  
  
 <span data-ttu-id="cc950-117">A seguinte tabela lista classes geralmente usadas ao trabalhar com o <xref:System.Xml.Xsl.XslTransform> e XPath e sua função.</span><span class="sxs-lookup"><span data-stu-id="cc950-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>  
  
|<span data-ttu-id="cc950-118">Classe ou interface</span><span class="sxs-lookup"><span data-stu-id="cc950-118">Class or Interface</span></span>|<span data-ttu-id="cc950-119">Função</span><span class="sxs-lookup"><span data-stu-id="cc950-119">Function</span></span>|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="cc950-120">É uma API que fornece um modelo de estilo de cursor para navegar em um repositório, junto com suporte a consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="cc950-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="cc950-121">Não fornece a edição do repositório subjacente.</span><span class="sxs-lookup"><span data-stu-id="cc950-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="cc950-122">Para editar, use a classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc950-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|  
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="cc950-123">É uma interface que fornece um método `CreateNavigator` para um <xref:System.Xml.XPath.XPathNavigator> para o repositório.</span><span class="sxs-lookup"><span data-stu-id="cc950-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|  
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="cc950-124">Ela permite a edição deste documento.</span><span class="sxs-lookup"><span data-stu-id="cc950-124">It enables editing of this document.</span></span> <span data-ttu-id="cc950-125">Implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo os cenários de edição de documento onde as transformações XSLT são necessárias posteriormente.</span><span class="sxs-lookup"><span data-stu-id="cc950-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="cc950-126">Para obter mais informações, consulte [entrada XmlDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="cc950-126">For more information, see [XmlDocument Input to XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span></span>|  
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="cc950-127">É derivada do <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="cc950-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="cc950-128">Ela faz a ponte sobre os mundos relacionais e XML usando <xref:System.Data.DataSet> para otimizar o armazenamento de dados estruturados dentro do documento XML de acordo com mapeamentos especificados no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="cc950-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc950-129">Ela implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo situações onde as transformações XSLT podem ser executadas sobre os dados relacionais recuperados de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cc950-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="cc950-130">Para obter mais informações, consulte [integração XML com dados relacionais e ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="cc950-130">For more information, see [XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span></span>|  
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="cc950-131">Essa classe é otimizada para processamento de <xref:System.Xml.Xsl.XslTransform> e consultas XPath, e fornece um cache somente leitura de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="cc950-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="cc950-132">Implementa <xref:System.Xml.XPath.IXPathNavigable> e é o repositório preferido a ser usado para transformações XSLT.</span><span class="sxs-lookup"><span data-stu-id="cc950-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="cc950-133">Fornece a navegação em conjuntos de nós XPath.</span><span class="sxs-lookup"><span data-stu-id="cc950-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="cc950-134">Todos os métodos de seleção XPath no <xref:System.Xml.XPath.XPathNavigator> retornam um <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="cc950-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="cc950-135">Vários objetos <xref:System.Xml.XPath.XPathNodeIterator> podem ser criados no mesmo repositório, cada um representando um conjunto de nós selecionado.</span><span class="sxs-lookup"><span data-stu-id="cc950-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|  
  
## <a name="msxml-xslt-extensions"></a><span data-ttu-id="cc950-136">Extensões de MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="cc950-136">MSXML XSLT Extensions</span></span>  
 <span data-ttu-id="cc950-137">As funções `msxsl:script` e `msxsl:node-set` são as únicas extensões XSLT do Microsoft XML Core Services (MSXML) com suporte pela classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="cc950-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc950-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc950-138">Example</span></span>  
 <span data-ttu-id="cc950-139">O exemplo de código a seguir carrega uma folha de estilos XSLT, lê um arquivo chamado mydata.xml em um <xref:System.Xml.XPath.XPathDocument> e executa uma transformação nos dados em um arquivo fictício chamado myStyleSheet.xsl, enviando a saída formatada para o console.</span><span class="sxs-lookup"><span data-stu-id="cc950-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
    Private filename As [String] = "mydata.xml"  
    Private stylesheet As [String] = "myStyleSheet.xsl"  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load(stylesheet)  
        Dim xpathdocument As New XPathDocument(filename)  
        Dim writer As New XmlTextWriter(Console.Out)  
        writer.Formatting = Formatting.Indented  
  
        xslt.Transform(xpathdocument, Nothing, writer, Nothing)  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample   
{  
    private const String filename = "mydata.xml";  
    private const String stylesheet = "myStyleSheet.xsl";  
  
    public static void Main()   
    {  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc950-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc950-140">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="cc950-141">Classe XslTransform implementa do processador XSLT</span><span class="sxs-lookup"><span data-stu-id="cc950-141">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="cc950-142">Implementação de comportamentos arbitrários na classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="cc950-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [<span data-ttu-id="cc950-143">XPathNavigator nas transformações</span><span class="sxs-lookup"><span data-stu-id="cc950-143">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="cc950-144">XPathNodeIterator nas transformações</span><span class="sxs-lookup"><span data-stu-id="cc950-144">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="cc950-145">Entrada XPathDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="cc950-145">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="cc950-146">Entrada de XmlDataDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="cc950-146">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="cc950-147">Entrada de XmlDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="cc950-147">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
