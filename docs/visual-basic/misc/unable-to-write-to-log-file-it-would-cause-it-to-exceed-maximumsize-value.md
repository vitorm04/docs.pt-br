---
title: "N&#227;o &#233; poss&#237;vel gravar no arquivo de log porque a grava&#231;&#227;o far&#225; com que ela ultrapasse o valor MaximumSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_FileExceedsMaximumSize"
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel gravar no arquivo de log porque a grava&#231;&#227;o far&#225; com que ela ultrapasse o valor MaximumSize
O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde gravar o arquivo de log porque:  
  
-   O tamanho do arquivo de log \(em bytes\) é maior que o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade  
  
     — e —  
  
-   O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.  
  
### Para corrigir este erro  
  
1.  Arquive os logs existentes e remova\-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.  
  
2.  Altere o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade para permitir logs maiores.  
  
3.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> para descartar as mensagens sem aviso se o log é muito grande.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)