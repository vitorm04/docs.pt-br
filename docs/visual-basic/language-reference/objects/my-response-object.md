---
title: Objeto My. Response (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 2f72f493d99c1e0b0469150c041649486e5ed124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818989"
---
# <a name="myresponse-object"></a>Objeto My.Response
Obtém o <xref:System.Web.HttpResponse> objeto associado com o <xref:System.Web.UI.Page>. Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  
 O `My.Response` atual do objeto contém <xref:System.Web.HttpResponse> objeto associado à página.  
  
 O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho de `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Web.HttpResponse>
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
