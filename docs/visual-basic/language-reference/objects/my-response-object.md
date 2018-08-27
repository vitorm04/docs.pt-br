---
title: Objeto My. Response (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: d5f49529a2593093a234babc22f64b591ea3cc61
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929545"
---
# <a name="myresponse-object"></a><span data-ttu-id="27d91-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="27d91-102">My.Response Object</span></span>
<span data-ttu-id="27d91-103">Obtém o <xref:System.Web.HttpResponse> objeto associado com o <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="27d91-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="27d91-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="27d91-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27d91-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="27d91-105">Remarks</span></span>  
 <span data-ttu-id="27d91-106">O `My.Response` atual do objeto contém <xref:System.Web.HttpResponse> objeto associado à página.</span><span class="sxs-lookup"><span data-stu-id="27d91-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="27d91-107">O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="27d91-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27d91-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27d91-108">Example</span></span>  
 <span data-ttu-id="27d91-109">O exemplo a seguir obtém a coleção de cabeçalho de `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="27d91-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="27d91-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27d91-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="27d91-111">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="27d91-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
