---
title: "Não é possível obter um fluxo para o log"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="da10c-102">Não é possível obter um fluxo para o log</span><span class="sxs-lookup"><span data-stu-id="da10c-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="da10c-103">Não é possível obter um fluxo para o log.</span><span class="sxs-lookup"><span data-stu-id="da10c-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="da10c-104">Possíveis nomes de arquivo com base em \<nome > já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="da10c-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="da10c-105">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não foi possível criar um novo arquivo de log porque todos os possíveis nomes de arquivo de log com base em \<nome > já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="da10c-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="da10c-106">Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da10c-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="da10c-107">Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="da10c-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da10c-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="da10c-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="da10c-109">Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> para incluir um carimbo de data no nome do arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="da10c-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="da10c-110">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.</span><span class="sxs-lookup"><span data-stu-id="da10c-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da10c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da10c-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="da10c-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="da10c-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="da10c-113">Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="da10c-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
