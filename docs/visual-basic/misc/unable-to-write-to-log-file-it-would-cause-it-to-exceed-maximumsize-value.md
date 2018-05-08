---
title: Não é possível gravar no arquivo de log porque a gravação faria com que ele exceder o valor MaximumSize
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: dabd9559864f9c04d7e4647f1e7da24adc679b24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Não é possível gravar no arquivo de log porque a gravação faria com que ele exceder o valor MaximumSize
O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não foi possível gravar o arquivo de log porque:  
  
-   O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade  
  
     — e —  
  
-   O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.  
  
2.  Alterar o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade para permitir logs maiores.  
  
3.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> para descartar as mensagens sem aviso se o log é muito grande.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [Info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
