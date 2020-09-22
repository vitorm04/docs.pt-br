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
# <a name="myrequest-object"></a>Objeto My.Request

Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.  
  
## <a name="remarks"></a>Comentários  

 O objeto `My.Request` contém informações sobre a solicitação HTTP atual.  
  
 O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` objeto e usa o `My.Response` objeto para escrevê-lo na página ASP.net.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Web.HttpRequest>
- [Objeto My.Response](my-response-object.md)
