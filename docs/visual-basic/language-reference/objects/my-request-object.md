---
title: Objeto My.Request
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: d0459506994fb69ebfaa4186ba137044b6fe9464
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870072"
---
# <a name="myrequest-object"></a><span data-ttu-id="0058a-102">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="0058a-102">My.Request Object</span></span>

<span data-ttu-id="0058a-103">Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.</span><span class="sxs-lookup"><span data-stu-id="0058a-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0058a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0058a-104">Remarks</span></span>  

 <span data-ttu-id="0058a-105">O objeto `My.Request` contém informações sobre a solicitação HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="0058a-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="0058a-106">O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0058a-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0058a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0058a-107">Example</span></span>  

 <span data-ttu-id="0058a-108">O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` objeto e usa o `My.Response` objeto para escrevê-lo na página ASP.net.</span><span class="sxs-lookup"><span data-stu-id="0058a-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0058a-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="0058a-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="0058a-110">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="0058a-110">My.Response Object</span></span>](my-response-object.md)
