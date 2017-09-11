---
title: Objeto My. Response | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
dev_langs:
- VB
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9b34c9df31536f6d553cda2e26677a2645768c2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="myresponse-object"></a><span data-ttu-id="37343-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="37343-102">My.Response Object</span></span>
<span data-ttu-id="37343-103">Obtém o <xref:System.Web.HttpResponse>objeto associado a <xref:System.Web.UI.Page>.</xref:System.Web.UI.Page> </xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="37343-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="37343-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="37343-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37343-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="37343-105">Remarks</span></span>  
 <span data-ttu-id="37343-106">O `My.Response` objeto contém atual <xref:System.Web.HttpResponse>objeto associado à página.</xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="37343-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="37343-107">O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="37343-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37343-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37343-108">Example</span></span>  
 <span data-ttu-id="37343-109">O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` e usa o `My.Response` objeto gravá-lo para a página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="37343-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 <span data-ttu-id="37343-110">[!code-vb[VbVbalrMyWeb n º&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span><span class="sxs-lookup"><span data-stu-id="37343-110">[!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37343-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37343-111">See Also</span></span>  
 <span data-ttu-id="37343-112"><xref:System.Web.HttpResponse></xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="37343-112"><xref:System.Web.HttpResponse></span></span>   
<span data-ttu-id="37343-113"> [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)</span><span class="sxs-lookup"><span data-stu-id="37343-113"> [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)</span></span>
