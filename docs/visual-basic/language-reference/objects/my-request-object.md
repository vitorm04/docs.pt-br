---
title: Objeto My.Request
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372421"
---
# <a name="myrequest-object"></a><span data-ttu-id="a91d7-102">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="a91d7-102">My.Request Object</span></span>
<span data-ttu-id="a91d7-103">Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.</span><span class="sxs-lookup"><span data-stu-id="a91d7-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a91d7-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a91d7-104">Remarks</span></span>  
 <span data-ttu-id="a91d7-105">O objeto `My.Request` contém informações sobre a solicitação HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="a91d7-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="a91d7-106">O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a91d7-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a91d7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a91d7-107">Example</span></span>  
 <span data-ttu-id="a91d7-108">O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` objeto e usa o `My.Response` objeto para escrevê-lo na página ASP.net.</span><span class="sxs-lookup"><span data-stu-id="a91d7-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a91d7-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="a91d7-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="a91d7-110">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="a91d7-110">My.Response Object</span></span>](my-response-object.md)
