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
# <a name="myresponse-object"></a>Objeto My.Response
Obtém o objeto <xref:System.Web.HttpResponse> associado ao <xref:System.Web.UI.Page>. Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.Response` contém o objeto <xref:System.Web.HttpResponse> atual associado à página.  
  
 O objeto `My.Response` só está disponível para aplicativos ASP.NET.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho do objeto `My.Request` e usa o objeto `My.Response` para gravá-lo na página ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Web.HttpResponse>
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
