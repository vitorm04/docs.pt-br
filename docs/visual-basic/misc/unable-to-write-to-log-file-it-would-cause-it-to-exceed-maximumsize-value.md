---
title: Não é possível gravar no arquivo de log porque a gravação faria com que ele exceder o valor MaximumSize
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: dabd9559864f9c04d7e4647f1e7da24adc679b24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640326"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="90906-102">Não é possível gravar no arquivo de log porque a gravação faria com que ele exceder o valor MaximumSize</span><span class="sxs-lookup"><span data-stu-id="90906-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="90906-103">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não foi possível gravar o arquivo de log porque:</span><span class="sxs-lookup"><span data-stu-id="90906-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="90906-104">O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="90906-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="90906-105">— e —</span><span class="sxs-lookup"><span data-stu-id="90906-105">—and—</span></span>  
  
-   <span data-ttu-id="90906-106">O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="90906-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90906-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="90906-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="90906-108">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.</span><span class="sxs-lookup"><span data-stu-id="90906-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="90906-109">Alterar o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> propriedade para permitir logs maiores.</span><span class="sxs-lookup"><span data-stu-id="90906-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3.  <span data-ttu-id="90906-110">Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> para descartar as mensagens sem aviso se o log é muito grande.</span><span class="sxs-lookup"><span data-stu-id="90906-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90906-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90906-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [<span data-ttu-id="90906-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="90906-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="90906-113">Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="90906-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
