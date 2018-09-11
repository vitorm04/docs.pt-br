---
title: Objeto My. Response (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: d5f49529a2593093a234babc22f64b591ea3cc61
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364917"
---
# <a name="myresponse-object"></a>Objeto My.Response
Obtém o <xref:System.Web.HttpResponse> objeto associado com o <xref:System.Web.UI.Page>. Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  
 O `My.Response` atual do objeto contém <xref:System.Web.HttpResponse> objeto associado à página.  
  
 O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho de `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Web.HttpResponse>  
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
