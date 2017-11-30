---
title: "Transformações XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="76db1-102">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="76db1-102">XSLT Transformations</span></span>
<span data-ttu-id="76db1-103">A linguagem XSL Transformation (XSLT) permite transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="76db1-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="76db1-104">Por exemplo, você pode usar XSLT para transformar XML em HTML para usar em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76db1-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="76db1-105">Esse processo de transformação é especificado pelo [recomendação do W3C XSLT (transformações XSL) versão 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="76db1-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="76db1-106">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76db1-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="76db1-107">A classe <xref:System.Xml.Xsl.XslCompiledTransform> oferece suporte à recomendação XSLT 1.0 do W3C.</span><span class="sxs-lookup"><span data-stu-id="76db1-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76db1-108">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="76db1-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="76db1-109">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é uma nova implementação do mecanismo do XSLT.</span><span class="sxs-lookup"><span data-stu-id="76db1-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="76db1-110">Ela inclui aprimoramentos de desempenho e novos recursos de segurança.</span><span class="sxs-lookup"><span data-stu-id="76db1-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="76db1-111">A prática recomendada é criar aplicativos do XSLT usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="76db1-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76db1-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="76db1-112">In This Section</span></span>  
 [<span data-ttu-id="76db1-113">Usando a classe de XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="76db1-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="76db1-114">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="76db1-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="76db1-115">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="76db1-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="76db1-116">Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="76db1-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="76db1-117">Compilador XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="76db1-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="76db1-118">Fornece informações sobre como usar o compilador do XSLT.</span><span class="sxs-lookup"><span data-stu-id="76db1-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="76db1-119">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="76db1-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="76db1-120">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="76db1-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="76db1-121">**Observação** o <xref:System.Xml.Xsl.XslTransform> classe está obsoleta na versão do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="76db1-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="76db1-122">Referência</span><span class="sxs-lookup"><span data-stu-id="76db1-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="76db1-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="76db1-123">Related Sections</span></span>  
 [<span data-ttu-id="76db1-124">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="76db1-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
