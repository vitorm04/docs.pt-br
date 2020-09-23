---
title: Não é possível gravar no arquivo de log porque isso faria com que ele excedesse o valor de MaximumSize
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 95a7b9036e7c1494cd44c250b0580bab5144417b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059451"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Não é possível gravar no arquivo de log porque isso faria com que ele excedesse o valor de MaximumSize

A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde gravar no arquivo de log porque:  
  
- O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> Propriedade  
  
     —e—  
  
- O valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> Propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto crie novos logs.  
  
2. Altere o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade para permitir logs maiores.  
  
3. Defina a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade como <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> para descartar mensagens sem aviso se o log for muito grande.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [Meu. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [Meu. Application. info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
