---
title: Não é possível gravar no arquivo de log porque a gravação para ele faria com que ele exceder o valor de MaximumSize
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 587b35282c7e78da1fdf4ccf9d08214e5665119c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022552"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="a66e9-102">Não é possível gravar no arquivo de log porque a gravação para ele faria com que ele exceder o valor de MaximumSize</span><span class="sxs-lookup"><span data-stu-id="a66e9-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="a66e9-103">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde gravar o arquivo de log porque:</span><span class="sxs-lookup"><span data-stu-id="a66e9-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="a66e9-104">O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="a66e9-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="a66e9-105">— e —</span><span class="sxs-lookup"><span data-stu-id="a66e9-105">—and—</span></span>  
  
- <span data-ttu-id="a66e9-106">O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="a66e9-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a66e9-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a66e9-107">To correct this error</span></span>  
  
1. <span data-ttu-id="a66e9-108">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.</span><span class="sxs-lookup"><span data-stu-id="a66e9-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="a66e9-109">Altere o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade para permitir que logs maiores.</span><span class="sxs-lookup"><span data-stu-id="a66e9-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="a66e9-110">Defina as <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade para <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> para descartar as mensagens sem aviso se o log é muito grande.</span><span class="sxs-lookup"><span data-stu-id="a66e9-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66e9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a66e9-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="a66e9-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="a66e9-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="a66e9-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="a66e9-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
