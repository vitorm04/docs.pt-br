---
title: Objeto My.Response
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76d0e701107add0d5bd468ba7a829759739e0cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="myresponse-object"></a><span data-ttu-id="27e87-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="27e87-102">My.Response Object</span></span>
<span data-ttu-id="27e87-103">Obtém o <xref:System.Web.HttpResponse> objeto associado a <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="27e87-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="27e87-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="27e87-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27e87-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="27e87-105">Remarks</span></span>  
 <span data-ttu-id="27e87-106">O `My.Response` atual do objeto contém <xref:System.Web.HttpResponse> objeto associado à página.</span><span class="sxs-lookup"><span data-stu-id="27e87-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="27e87-107">O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="27e87-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e87-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27e87-108">Example</span></span>  
 <span data-ttu-id="27e87-109">O exemplo a seguir obtém a coleção de cabeçalho a `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="27e87-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="27e87-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27e87-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="27e87-111">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="27e87-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
