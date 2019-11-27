---
title: Objeto My.Request
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 22329bc501c9bb75b1336dd5384ab5b23a98ac21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350687"
---
# <a name="myrequest-object"></a>Objeto My.Request
Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.Request` contém informações sobre a solicitação HTTP atual.  
  
 O objeto `My.Request` está disponível somente para aplicativos do ASP.NET.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho do objeto `My.Request` e usa o objeto `My.Response` para gravá-lo na página ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Web.HttpRequest>
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
