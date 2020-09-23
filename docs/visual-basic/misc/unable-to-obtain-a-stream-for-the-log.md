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
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="13f42-102">Não é possível obter um fluxo para o log</span><span class="sxs-lookup"><span data-stu-id="13f42-102">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="13f42-103">Não é possível obter um fluxo para o log.</span><span class="sxs-lookup"><span data-stu-id="13f42-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="13f42-104">Os nomes de arquivo potenciais com base em \<name> já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="13f42-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="13f42-105">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde criar um novo arquivo de log porque todos os nomes de arquivo de log potenciais com base no \<name> já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="13f42-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="13f42-106">Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13f42-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="13f42-107">Consulte a documentação da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="13f42-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13f42-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="13f42-108">To correct this error</span></span>  
  
1. <span data-ttu-id="13f42-109">Defina a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade como <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> para incluir um carimbo de data/hora no nome do arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="13f42-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="13f42-110">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto crie novos logs.</span><span class="sxs-lookup"><span data-stu-id="13f42-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f42-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="13f42-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="13f42-112">Meu. Application. log</span><span class="sxs-lookup"><span data-stu-id="13f42-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="13f42-113">Meu. Application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="13f42-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
