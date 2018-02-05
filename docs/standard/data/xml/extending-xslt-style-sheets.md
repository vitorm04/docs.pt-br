---
title: Estendendo folhas de estilos XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aea28532dd81745b8d018cbeed454bbd008c8ed7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="e9885-102">Estendendo folhas de estilos XSLT</span><span class="sxs-lookup"><span data-stu-id="e9885-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="e9885-103">Esta seção descreve os diferentes métodos de estender a funcionalidade de fonte.</span><span class="sxs-lookup"><span data-stu-id="e9885-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="e9885-104">Você pode adicionar objetos ou parâmetros de extensão usando a classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="e9885-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="e9885-105">Os objetos ou parâmetros de extensão podem ser chamados de folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="e9885-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="e9885-106">Além disso, você também pode inserir blocos de script na folha de estilos usando o elemento de `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="e9885-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9885-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e9885-107">In This Section</span></span>  
 [<span data-ttu-id="e9885-108">Objetos de extensão de XSLT</span><span class="sxs-lookup"><span data-stu-id="e9885-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="e9885-109">Discute o uso da classe de <xref:System.Xml.Xsl.XsltArgumentList> para processar objetos de extensão XSLT.</span><span class="sxs-lookup"><span data-stu-id="e9885-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="e9885-110">Parâmetros de XSLT</span><span class="sxs-lookup"><span data-stu-id="e9885-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="e9885-111">Discute o uso da classe de <xref:System.Xml.Xsl.XsltArgumentList> para processar parâmetros XSLT.</span><span class="sxs-lookup"><span data-stu-id="e9885-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="e9885-112">Blocos de script usando msxsl:script</span><span class="sxs-lookup"><span data-stu-id="e9885-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="e9885-113">Discute usando o elemento de `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="e9885-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9885-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e9885-114">Related Sections</span></span>  
 [<span data-ttu-id="e9885-115">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="e9885-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
