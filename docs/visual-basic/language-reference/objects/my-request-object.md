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
# <a name="myrequest-object"></a>Objeto My.Request
Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.Request` contém informações sobre a solicitação HTTP atual.  
  
 O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho de `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Web.HttpRequest>
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
