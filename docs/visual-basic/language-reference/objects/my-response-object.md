---
title: Meu objeto. Response (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567457"
---
# <a name="myresponse-object"></a><span data-ttu-id="cfb18-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="cfb18-102">My.Response Object</span></span>
<span data-ttu-id="cfb18-103">Obtém o <xref:System.Web.HttpResponse> objeto associado <xref:System.Web.UI.Page>ao.</span><span class="sxs-lookup"><span data-stu-id="cfb18-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="cfb18-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="cfb18-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb18-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfb18-105">Remarks</span></span>  
 <span data-ttu-id="cfb18-106">O `My.Response` objeto contém o objeto <xref:System.Web.HttpResponse> atual associado à página.</span><span class="sxs-lookup"><span data-stu-id="cfb18-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="cfb18-107">O `My.Response` objeto só está disponível para aplicativos ASP.net.</span><span class="sxs-lookup"><span data-stu-id="cfb18-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfb18-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfb18-108">Example</span></span>  
 <span data-ttu-id="cfb18-109">O exemplo a seguir obtém a coleção de cabeçalho `My.Request` do objeto e usa `My.Response` o objeto para escrevê-lo na página ASP.net.</span><span class="sxs-lookup"><span data-stu-id="cfb18-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb18-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfb18-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="cfb18-111">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="cfb18-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
