---
title: "Objeto My.Request | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.MyWebExtension.Request"
  - "My.Request"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My.Request"
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objeto My.Request
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.  
  
## Comentários  
 O objeto `My.Request` contém informações sobre o solicitação HTTP atual.  
  
 O objeto `My.Request` está disponível somente para aplicativos ASP.NET.  
  
## Exemplo  
 O exemplo a seguir obtém a coleção de cabeçalho do objeto `My.Request` e usa o objeto `My.Response` para gravá\-la na página ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## Consulte também  
 <xref:System.Web.HttpRequest>   
 [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)