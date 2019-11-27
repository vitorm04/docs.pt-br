---
title: Objeto My.Response
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350652"
---
# <a name="myresponse-object"></a><span data-ttu-id="3c904-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="3c904-102">My.Response Object</span></span>
<span data-ttu-id="3c904-103">Obtém o objeto <xref:System.Web.HttpResponse> associado ao <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="3c904-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="3c904-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="3c904-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c904-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c904-105">Remarks</span></span>  
 <span data-ttu-id="3c904-106">O objeto `My.Response` contém o objeto <xref:System.Web.HttpResponse> atual associado à página.</span><span class="sxs-lookup"><span data-stu-id="3c904-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="3c904-107">O objeto `My.Response` só está disponível para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c904-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c904-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c904-108">Example</span></span>  
 <span data-ttu-id="3c904-109">O exemplo a seguir obtém a coleção de cabeçalho do objeto `My.Request` e usa o objeto `My.Response` para gravá-lo na página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c904-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3c904-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c904-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="3c904-111">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="3c904-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
