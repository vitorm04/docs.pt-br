---
title: Não é possível obter um fluxo para o log
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 540ff3fbba72d33b2efaa58ad7a8019628f5e83f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344748"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="15ff6-102">Não é possível obter um fluxo para o log</span><span class="sxs-lookup"><span data-stu-id="15ff6-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="15ff6-103">Não é possível obter um fluxo para o log.</span><span class="sxs-lookup"><span data-stu-id="15ff6-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="15ff6-104">Possíveis nomes de arquivo com base em \<nome > já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="15ff6-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="15ff6-105">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não foi possível criar um novo arquivo de log porque todos os possíveis nomes de arquivo de log com base em \<nome > já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="15ff6-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="15ff6-106">Ter muitos arquivos de log pode indicar um problema com o aplicativo de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="15ff6-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="15ff6-107">Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="15ff6-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15ff6-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="15ff6-108">To correct this error</span></span>  
  
1. <span data-ttu-id="15ff6-109">Defina as <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade para <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> para incluir um carimbo de data no nome do arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="15ff6-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="15ff6-110">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.</span><span class="sxs-lookup"><span data-stu-id="15ff6-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ff6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15ff6-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="15ff6-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="15ff6-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="15ff6-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="15ff6-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
