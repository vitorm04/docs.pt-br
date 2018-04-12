---
title: Objeto My.Response
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76d0e701107add0d5bd468ba7a829759739e0cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="myresponse-object"></a>Objeto My.Response
Obtém o <xref:System.Web.HttpResponse> objeto associado a <xref:System.Web.UI.Page>. Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  
 O `My.Response` atual do objeto contém <xref:System.Web.HttpResponse> objeto associado à página.  
  
 O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho a `My.Request` objeto e usa o `My.Response` objeto gravá-lo para a página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Web.HttpResponse>  
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
