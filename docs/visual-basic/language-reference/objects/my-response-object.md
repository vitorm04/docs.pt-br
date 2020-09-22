---
title: Objeto My.Response
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870042"
---
# <a name="myresponse-object"></a>Objeto My.Response

Obtém o <xref:System.Web.HttpResponse> objeto associado ao <xref:System.Web.UI.Page> . Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  

 O `My.Response` objeto contém o <xref:System.Web.HttpResponse> objeto atual associado à página.  
  
 O `My.Response` objeto só está disponível para aplicativos ASP.net.  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` objeto e usa o `My.Response` objeto para escrevê-lo na página ASP.net.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Web.HttpResponse>
- [Objeto My.Request](my-request-object.md)
