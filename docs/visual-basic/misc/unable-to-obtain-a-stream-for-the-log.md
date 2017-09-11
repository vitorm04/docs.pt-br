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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d210815c20cd288917394508fa5fb99535648a24
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="8d5ee-102">Não é possível obter um fluxo para o log</span><span class="sxs-lookup"><span data-stu-id="8d5ee-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="8d5ee-103">Não é possível obter um fluxo para o log.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="8d5ee-104">Possíveis nomes de arquivo com base em \<nome > já estão em uso.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="8d5ee-105">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde criar um novo arquivo de log porque todos os possíveis nomes de arquivo de log com base em \<nome > já estão em uso.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="8d5ee-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="8d5ee-106">Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="8d5ee-107">Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe para obter mais informações.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="8d5ee-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d5ee-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8d5ee-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="8d5ee-109">Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>propriedade <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>para incluir um carimbo de data no nome do arquivo de log.</xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> </xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A></span><span class="sxs-lookup"><span data-stu-id="8d5ee-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="8d5ee-110">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="8d5ee-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5ee-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d5ee-111">See Also</span></span>  
 <span data-ttu-id="8d5ee-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="8d5ee-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span></span>   
 <span data-ttu-id="8d5ee-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A></span><span class="sxs-lookup"><span data-stu-id="8d5ee-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A></span></span>   
<span data-ttu-id="8d5ee-114"> [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md) </span><span class="sxs-lookup"><span data-stu-id="8d5ee-114"> [My.Application.Log Object](../../visual-basic/language-reference/objects/my-application-log-object.md) </span></span>  
<span data-ttu-id="8d5ee-115"> [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)</span><span class="sxs-lookup"><span data-stu-id="8d5ee-115"> [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)</span></span>
