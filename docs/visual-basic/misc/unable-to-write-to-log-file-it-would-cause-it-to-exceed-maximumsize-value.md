---
title: "Não é possível gravar no arquivo de log porque a gravação fará com que ela ultrapasse o valor MaximumSize | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4bd32fb3b56ec8a992a7aa7fb6812a2ba8f04edc
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Não é possível gravar no arquivo de log porque a gravação fará com que ela ultrapasse o valor MaximumSize
O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde gravar o arquivo de log porque:</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
-   O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>propriedade</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
  
     — e —  
  
-   O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade foi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
2.  Altere o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>propriedade para permitir logs maiores.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
  
3.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>para descartar as mensagens sem aviso se o log é muito grande.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)
