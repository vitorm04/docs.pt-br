---
title: Transformações XSLT com a classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d534553fcc6ee63d560e731a535d44c3acd1a214
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347903"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="5faaa-102">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="5faaa-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="5faaa-103">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5faaa-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="5faaa-104">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5faaa-105">Confira [Usar a classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="5faaa-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="5faaa-106">O objetivo do XSLT é transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura (por exemplo, para transformar XML em HTML para uso em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo).</span><span class="sxs-lookup"><span data-stu-id="5faaa-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="5faaa-107">Este processo de transformação é especificado pela [recomendação de XSLT versão 1.0](https://www.w3.org/TR/1999/REC-xslt-19991116) do W3C (World Wide Web Consortium).</span><span class="sxs-lookup"><span data-stu-id="5faaa-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="5faaa-108">No .NET Framework, a classe <xref:System.Xml.Xsl.XslTransform>, localizada no namespace <xref:System.Xml.Xsl> é o processador XSLT que implementa a funcionalidade dessa especificação.</span><span class="sxs-lookup"><span data-stu-id="5faaa-108">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="5faaa-109">Há um pequeno número de recursos que não foram implementados da recomendação XSLT 1.0 do W3C, listada em [Saída de um XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="5faaa-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="5faaa-110">A figura a seguir mostra a arquitetura de transformação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5faaa-110">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="5faaa-111">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="5faaa-111">Overview</span></span>

![Diagrama que mostra a arquitetura de transformação XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="5faaa-113">A recomendação XSLT usa a linguagem XPath para selecionar partes de um documento XML, onde XPath é uma linguagem de consulta usada para navegar em nós de uma árvore do documento.</span><span class="sxs-lookup"><span data-stu-id="5faaa-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="5faaa-114">Conforme mostrado no diagrama, a implementação de XPath do .NET Framework é usada para selecionar partes de XML armazenadas em várias classes, como um <xref:System.Xml.XmlDocument>, um <xref:System.Xml.XmlDataDocument> e um <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-114">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="5faaa-115">Um <xref:System.Xml.XPath.XPathDocument> é um repositório de dados XSLT otimizado e, quando usado com <xref:System.Xml.Xsl.XslTransform>, fornece transformações XSLT com bom desempenho.</span><span class="sxs-lookup"><span data-stu-id="5faaa-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="5faaa-116">A seguinte tabela lista classes geralmente usadas ao trabalhar com o <xref:System.Xml.Xsl.XslTransform> e XPath e sua função.</span><span class="sxs-lookup"><span data-stu-id="5faaa-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="5faaa-117">Classe ou interface</span><span class="sxs-lookup"><span data-stu-id="5faaa-117">Class or Interface</span></span>|<span data-ttu-id="5faaa-118">Função</span><span class="sxs-lookup"><span data-stu-id="5faaa-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="5faaa-119">É uma API que fornece um modelo de estilo de cursor para navegar em um repositório, junto com suporte a consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="5faaa-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="5faaa-120">Não fornece a edição do repositório subjacente.</span><span class="sxs-lookup"><span data-stu-id="5faaa-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="5faaa-121">Para editar, use a classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="5faaa-122">É uma interface que fornece um método `CreateNavigator` para um <xref:System.Xml.XPath.XPathNavigator> para o repositório.</span><span class="sxs-lookup"><span data-stu-id="5faaa-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="5faaa-123">Ela permite a edição deste documento.</span><span class="sxs-lookup"><span data-stu-id="5faaa-123">It enables editing of this document.</span></span> <span data-ttu-id="5faaa-124">Implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo os cenários de edição de documento onde as transformações XSLT são necessárias posteriormente.</span><span class="sxs-lookup"><span data-stu-id="5faaa-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="5faaa-125">Para saber mais, consulte [Entrada de XmlDocument para XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="5faaa-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="5faaa-126">É derivada do <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="5faaa-127">Ela faz a ponte sobre os mundos relacionais e XML usando <xref:System.Data.DataSet> para otimizar o armazenamento de dados estruturados dentro do documento XML de acordo com mapeamentos especificados no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5faaa-128">Ela implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo situações onde as transformações XSLT podem ser executadas sobre os dados relacionais recuperados de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5faaa-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="5faaa-129">Para saber mais, confira [Integração XML com dados relacionais e ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="5faaa-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="5faaa-130">Essa classe é otimizada para processamento de <xref:System.Xml.Xsl.XslTransform> e consultas XPath, e fornece um cache somente leitura de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="5faaa-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="5faaa-131">Implementa <xref:System.Xml.XPath.IXPathNavigable> e é o repositório preferido a ser usado para transformações XSLT.</span><span class="sxs-lookup"><span data-stu-id="5faaa-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="5faaa-132">Fornece a navegação em conjuntos de nós XPath.</span><span class="sxs-lookup"><span data-stu-id="5faaa-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="5faaa-133">Todos os métodos de seleção XPath no <xref:System.Xml.XPath.XPathNavigator> retornam um <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="5faaa-134">Vários objetos <xref:System.Xml.XPath.XPathNodeIterator> podem ser criados no mesmo repositório, cada um representando um conjunto de nós selecionado.</span><span class="sxs-lookup"><span data-stu-id="5faaa-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="5faaa-135">Extensões de MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="5faaa-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="5faaa-136">As funções `msxsl:script` e `msxsl:node-set` são as únicas extensões XSLT do Microsoft XML Core Services (MSXML) com suporte pela classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="5faaa-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="5faaa-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5faaa-137">Example</span></span>

<span data-ttu-id="5faaa-138">O exemplo de código a seguir carrega uma folha de estilos XSLT, lê um arquivo chamado mydata.xml em um <xref:System.Xml.XPath.XPathDocument> e executa uma transformação nos dados em um arquivo fictício chamado myStyleSheet.xsl, enviando a saída formatada para o console.</span><span class="sxs-lookup"><span data-stu-id="5faaa-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
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
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5faaa-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5faaa-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="5faaa-140">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="5faaa-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="5faaa-141">Implementação de comportamentos discricionários na classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="5faaa-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="5faaa-142">XPathNavigator em transformações</span><span class="sxs-lookup"><span data-stu-id="5faaa-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="5faaa-143">XPathNodeIterator em transformações</span><span class="sxs-lookup"><span data-stu-id="5faaa-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="5faaa-144">Entrada de XPathDocument para XslTransform</span><span class="sxs-lookup"><span data-stu-id="5faaa-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="5faaa-145">Entrada de XmlDataDocument para XslTransform</span><span class="sxs-lookup"><span data-stu-id="5faaa-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="5faaa-146">Entrada de XmlDocument para XslTransform</span><span class="sxs-lookup"><span data-stu-id="5faaa-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
