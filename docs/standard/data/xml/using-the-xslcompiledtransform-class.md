---
title: Usando a classe XslCompiledTransform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a5c71a7796790343bf39de5bbfd03997c25d5f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="9e297-102">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9e297-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="9e297-103">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e297-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="9e297-104">Essa classe é usada para compilar folhas de estilos e executar transformações XSLT.</span><span class="sxs-lookup"><span data-stu-id="9e297-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e297-105">Embora o desempenho geral da classe <xref:System.Xml.Xsl.XslCompiledTransform> seja melhor do que o da classe <xref:System.Xml.Xsl.XslTransform>, o método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> da classe <xref:System.Xml.Xsl.XslCompiledTransform> possivelmente apresentará um desempenho mais lento do que o método <xref:System.Xml.Xsl.XslTransform.Load%2A> da classe <xref:System.Xml.Xsl.XslTransform> na primeira vez que for chamado em uma transformação.</span><span class="sxs-lookup"><span data-stu-id="9e297-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="9e297-106">Isso ocorre porque o arquivo XSLT deve ser compilado antes que seja carregado.</span><span class="sxs-lookup"><span data-stu-id="9e297-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="9e297-107">Para obter mais informações, consulte o seguinte postagem de blog: [XslCompiledTransform mais lenta que XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span><span class="sxs-lookup"><span data-stu-id="9e297-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e297-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9e297-108">In This Section</span></span>  
 [<span data-ttu-id="9e297-109">Entradas para a classe de XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9e297-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="9e297-110">Descreve as opções de entrada XSLT disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9e297-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="9e297-111">Opções de saída na classe de XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9e297-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="9e297-112">Descreve as opções de saída XSLT disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9e297-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="9e297-113">Resolvendo recursos externos durante processamento XSLT</span><span class="sxs-lookup"><span data-stu-id="9e297-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="9e297-114">Aborda o uso da classe <xref:System.Xml.XmlResolver> para resolver recursos externos.</span><span class="sxs-lookup"><span data-stu-id="9e297-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="9e297-115">Estendendo folhas de estilos XSLT</span><span class="sxs-lookup"><span data-stu-id="9e297-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="9e297-116">Aborda o suporte às extensões XSLT.</span><span class="sxs-lookup"><span data-stu-id="9e297-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="9e297-117">Erros recuperáveis XSLT</span><span class="sxs-lookup"><span data-stu-id="9e297-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="9e297-118">Lista os comportamentos discricionários permitidos pela recomendação da World Wide Web Consortium (W3C) XSLT 1.0 e descreve como esses comportamentos são tratados pela classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="9e297-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="9e297-119">Como: transformar um fragmento do nó</span><span class="sxs-lookup"><span data-stu-id="9e297-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="9e297-120">Descreve como transformar um fragmento de nó.</span><span class="sxs-lookup"><span data-stu-id="9e297-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="9e297-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9e297-121">Related Sections</span></span>  
 [<span data-ttu-id="9e297-122">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="9e297-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="9e297-123">Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform></span><span class="sxs-lookup"><span data-stu-id="9e297-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e297-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e297-124">See Also</span></span>  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
