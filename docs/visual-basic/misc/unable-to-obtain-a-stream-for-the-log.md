---
title: Não é possível obter um fluxo para o log
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 887356fac3abe5c9d28751f7c4d3b1908ed35acb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078379"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Não é possível obter um fluxo para o log

Não é possível obter um fluxo para o log. Os nomes de arquivo potenciais com base em \<name> já estão em uso.  
  
 A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde criar um novo arquivo de log porque todos os nomes de arquivo de log potenciais com base no \<name> já estão em uso.  
  
 Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo. Consulte a documentação da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Defina a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade como <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> para incluir um carimbo de data/hora no nome do arquivo de log.  
  
2. Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto crie novos logs.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [Meu. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [Meu. Application. info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
