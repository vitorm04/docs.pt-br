---
title: Objeto My. Request (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 08212dc5fe563ce84be02ab706b56195a0636894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836617"
---
# <a name="myrequest-object"></a><span data-ttu-id="a76c9-102">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="a76c9-102">My.Request Object</span></span>
<span data-ttu-id="a76c9-103">Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.</span><span class="sxs-lookup"><span data-stu-id="a76c9-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a76c9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a76c9-104">Remarks</span></span>  
 <span data-ttu-id="a76c9-105">O objeto `My.Request` contém informações sobre a solicitação HTTP atual.</span><span class="sxs-lookup"><span data-stu-id="a76c9-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="a76c9-106">O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a76c9-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a76c9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a76c9-107">Example</span></span>  
 <span data-ttu-id="a76c9-108">O exemplo a seguir obtém a coleção de cabeçalho de `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a76c9-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a76c9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a76c9-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="a76c9-110">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="a76c9-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
