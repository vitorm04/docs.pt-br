---
title: "Não é possível obter um fluxo para o log"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Não é possível obter um fluxo para o log
Não é possível obter um fluxo para o log. Possíveis nomes de arquivo com base em \<nome > já estão em uso.  
  
 O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não foi possível criar um novo arquivo de log porque todos os possíveis nomes de arquivo de log com base em \<nome > já estão em uso.  
  
 Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo. Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> para incluir um carimbo de data no nome do arquivo de log.  
  
2.  Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)
