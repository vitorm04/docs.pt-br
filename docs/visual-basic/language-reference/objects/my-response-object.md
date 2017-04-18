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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2ae9a659bb7575023dfa1847c9d405d0f7d6ac3
ms.lasthandoff: 03/13/2017

---
# <a name="myresponse-object"></a>Objeto My.Response
Obtém o <xref:System.Web.HttpResponse>objeto associado a <xref:System.Web.UI.Page>.</xref:System.Web.UI.Page> </xref:System.Web.HttpResponse> Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.  
  
## <a name="remarks"></a>Comentários  
 O `My.Response` objeto contém atual <xref:System.Web.HttpResponse>objeto associado à página.</xref:System.Web.HttpResponse>  
  
 O `My.Response` objeto só está disponível para [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] aplicativos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` e usa o `My.Response` objeto gravá-lo para a página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb n º&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Web.HttpResponse></xref:System.Web.HttpResponse>   
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
