---
title: Estendendo folhas de estilos XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff952df59dc8291b12df2b238052d4c40c834e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568817"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="37234-102">Estendendo folhas de estilos XSLT</span><span class="sxs-lookup"><span data-stu-id="37234-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="37234-103">Esta seção descreve os diferentes métodos de estender a funcionalidade de fonte.</span><span class="sxs-lookup"><span data-stu-id="37234-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="37234-104">Você pode adicionar objetos ou parâmetros de extensão usando a classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="37234-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="37234-105">Os objetos ou parâmetros de extensão podem ser chamados de folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="37234-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="37234-106">Além disso, você também pode inserir blocos de script na folha de estilos usando o elemento de `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="37234-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37234-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="37234-107">In This Section</span></span>  
 [<span data-ttu-id="37234-108">Objetos de extensão de XSLT</span><span class="sxs-lookup"><span data-stu-id="37234-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="37234-109">Discute o uso da classe de <xref:System.Xml.Xsl.XsltArgumentList> para processar objetos de extensão XSLT.</span><span class="sxs-lookup"><span data-stu-id="37234-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="37234-110">Parâmetros de XSLT</span><span class="sxs-lookup"><span data-stu-id="37234-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="37234-111">Discute o uso da classe de <xref:System.Xml.Xsl.XsltArgumentList> para processar parâmetros XSLT.</span><span class="sxs-lookup"><span data-stu-id="37234-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="37234-112">Blocos de script usando msxsl:script</span><span class="sxs-lookup"><span data-stu-id="37234-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="37234-113">Discute usando o elemento de `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="37234-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37234-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="37234-114">Related Sections</span></span>  
 [<span data-ttu-id="37234-115">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="37234-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
