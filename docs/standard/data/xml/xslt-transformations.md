---
title: Transformações XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 922de11567af9409265ee18bfa6a2637951c57c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570986"
---
# <a name="xslt-transformations"></a><span data-ttu-id="1b983-102">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="1b983-102">XSLT Transformations</span></span>
<span data-ttu-id="1b983-103">A linguagem XSL Transformation (XSLT) permite transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="1b983-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="1b983-104">Por exemplo, você pode usar XSLT para transformar XML em HTML para usar em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b983-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="1b983-105">Esse processo de transformação é especificado pela [Recomendação da linguagem XSL Transformations (XSLT) do W3C Versão 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="1b983-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="1b983-106">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT no .NET.</span><span class="sxs-lookup"><span data-stu-id="1b983-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="1b983-107">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é compatível com a [recomendação XSLT 1.0 do W3C](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="1b983-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b983-108">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="1b983-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="1b983-109">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é uma nova implementação do mecanismo do XSLT.</span><span class="sxs-lookup"><span data-stu-id="1b983-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="1b983-110">Ela inclui aprimoramentos de desempenho e novos recursos de segurança.</span><span class="sxs-lookup"><span data-stu-id="1b983-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="1b983-111">A prática recomendada é criar aplicativos do XSLT usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1b983-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b983-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1b983-112">In This Section</span></span>  
 [<span data-ttu-id="1b983-113">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="1b983-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="1b983-114">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1b983-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="1b983-115">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="1b983-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="1b983-116">Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="1b983-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="1b983-117">Compilador de XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="1b983-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="1b983-118">Fornece informações sobre como usar o compilador do XSLT.</span><span class="sxs-lookup"><span data-stu-id="1b983-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="1b983-119">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="1b983-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="1b983-120">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="1b983-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1b983-121">Referência</span><span class="sxs-lookup"><span data-stu-id="1b983-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="1b983-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1b983-122">Related Sections</span></span>  
 [<span data-ttu-id="1b983-123">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="1b983-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
