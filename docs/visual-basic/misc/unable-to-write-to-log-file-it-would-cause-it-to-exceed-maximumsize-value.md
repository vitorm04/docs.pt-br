---
title: "Não é possível gravar no arquivo de log porque a gravação fará com que ela ultrapasse o valor MaximumSize | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
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
ms.openlocfilehash: bb2434c5028f6e9ca3369d17f60ffac0a00d137b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="736c6-102">Não é possível gravar no arquivo de log porque a gravação fará com que ela ultrapasse o valor MaximumSize</span><span class="sxs-lookup"><span data-stu-id="736c6-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="736c6-103">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde gravar o arquivo de log porque:</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="736c6-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="736c6-104">O tamanho do arquivo de log (em bytes) é maior que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>propriedade</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="736c6-105">— e —</span><span class="sxs-lookup"><span data-stu-id="736c6-105">—and—</span></span>  
  
-   <span data-ttu-id="736c6-106">O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade foi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="736c6-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="736c6-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="736c6-108">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="736c6-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="736c6-109">Altere o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>propriedade para permitir logs maiores.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3.  <span data-ttu-id="736c6-110">Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>para descartar as mensagens sem aviso se o log é muito grande.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="736c6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="736c6-111">See Also</span></span>  
 <span data-ttu-id="736c6-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span></span>   
 <span data-ttu-id="736c6-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="736c6-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span></span>   
 <span data-ttu-id="736c6-114"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="736c6-114"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span></span>   
<span data-ttu-id="736c6-115"> [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md) </span><span class="sxs-lookup"><span data-stu-id="736c6-115"> [My.Application.Log Object](../../visual-basic/language-reference/objects/my-application-log-object.md) </span></span>  
<span data-ttu-id="736c6-116"> [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)</span><span class="sxs-lookup"><span data-stu-id="736c6-116"> [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)</span></span>
