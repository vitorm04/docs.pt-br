---
title: "Não é possível gravar no arquivo de log porque a gravação reduziria espaço livre em disco abaixo do valor de ReservedSpace | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 9
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
ms.openlocfilehash: 9e2d923751ed21656690dc0833cff2844ddc1f48
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a>Não é possível gravar no arquivo de log porque a gravação reduziria espaço livre em disco abaixo do valor de ReservedSpace
O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde gravar o arquivo de log porque:</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
-   A quantidade de espaço livre em disco (em bytes) é menor que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>propriedade</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
  
     — e —  
  
-   O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade foi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
2.  Altere o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>propriedade para um número menor para reservar menos espaço em disco.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
  
3.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>para descartar as mensagens sem aviso se não houver espaço em disco suficiente.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)
