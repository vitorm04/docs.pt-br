---
title: "Não é possível obter um fluxo para o log | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
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
ms.openlocfilehash: 1afb5855f2fefd94b9fa74d32c8894bba9e4bc4f
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Não é possível obter um fluxo para o log
Não é possível obter um fluxo para o log. Possíveis nomes de arquivo com base em \<nome > já estão em uso.  
  
 O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde criar um novo arquivo de log porque todos os possíveis nomes de arquivo de log com base em \<nome > já estão em uso.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
 Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo. Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe para obter mais informações.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>propriedade <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>para incluir um carimbo de data no nome do arquivo de log.</xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> </xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
  
2.  Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)
