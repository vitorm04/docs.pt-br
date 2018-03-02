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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92d0688b86e6a95af46e09c21c1a8b3cdf66efc3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="231a7-102">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="231a7-102">XSLT Transformations</span></span>
<span data-ttu-id="231a7-103">A linguagem XSL Transformation (XSLT) permite transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="231a7-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="231a7-104">Por exemplo, você pode usar XSLT para transformar XML em HTML para usar em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="231a7-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="231a7-105">Esse processo de transformação é especificado pela [Recomendação da linguagem XSL Transformations (XSLT) do W3C Versão 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="231a7-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="231a7-106">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="231a7-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="231a7-107">A classe <xref:System.Xml.Xsl.XslCompiledTransform> oferece suporte à recomendação XSLT 1.0 do W3C.</span><span class="sxs-lookup"><span data-stu-id="231a7-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="231a7-108">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="231a7-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="231a7-109">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é uma nova implementação do mecanismo do XSLT.</span><span class="sxs-lookup"><span data-stu-id="231a7-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="231a7-110">Ela inclui aprimoramentos de desempenho e novos recursos de segurança.</span><span class="sxs-lookup"><span data-stu-id="231a7-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="231a7-111">A prática recomendada é criar aplicativos do XSLT usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="231a7-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="231a7-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="231a7-112">In This Section</span></span>  
 [<span data-ttu-id="231a7-113">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="231a7-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="231a7-114">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="231a7-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="231a7-115">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="231a7-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="231a7-116">Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="231a7-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="231a7-117">Compilador de XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="231a7-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="231a7-118">Fornece informações sobre como usar o compilador do XSLT.</span><span class="sxs-lookup"><span data-stu-id="231a7-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="231a7-119">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="231a7-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="231a7-120">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="231a7-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="231a7-121">**Observação<xref:System.Xml.Xsl.XslTransform> A classe**  está obsoleta na versão 2.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="231a7-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="231a7-122">Referência</span><span class="sxs-lookup"><span data-stu-id="231a7-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="231a7-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="231a7-123">Related Sections</span></span>  
 [<span data-ttu-id="231a7-124">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="231a7-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
