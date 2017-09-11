---
title: "Não é possível gravar no arquivo de log porque a gravação reduziria espaço livre em disco abaixo do valor de ReservedSpace | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 9
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
ms.openlocfilehash: 5826fe24eb5aaeadedb956259b6ce1a1f9025130
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="394b8-102">Não é possível gravar no arquivo de log porque a gravação reduziria espaço livre em disco abaixo do valor de ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="394b8-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="394b8-103">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>classe não pôde gravar o arquivo de log porque:</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="394b8-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="394b8-104">A quantidade de espaço livre em disco (em bytes) é menor que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>propriedade</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="394b8-105">— e —</span><span class="sxs-lookup"><span data-stu-id="394b8-105">—and—</span></span>  
  
-   <span data-ttu-id="394b8-106">O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade foi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="394b8-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="394b8-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="394b8-108">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>objeto para criar novos logs.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="394b8-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="394b8-109">Altere o valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>propriedade para um número menor para reservar menos espaço em disco.</xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3.  <span data-ttu-id="394b8-110">Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>propriedade <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>para descartar as mensagens sem aviso se não houver espaço em disco suficiente.</xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> </xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394b8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="394b8-111">See Also</span></span>  
 <span data-ttu-id="394b8-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-112"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span></span>   
 <span data-ttu-id="394b8-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="394b8-113"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A></span></span>   
 <span data-ttu-id="394b8-114"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="394b8-114"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener></span></span>   
<span data-ttu-id="394b8-115"> [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md) </span><span class="sxs-lookup"><span data-stu-id="394b8-115"> [My.Application.Log Object](../../visual-basic/language-reference/objects/my-application-log-object.md) </span></span>  
<span data-ttu-id="394b8-116"> [Objeto My.Log](../../visual-basic/language-reference/objects/my-log-object.md)</span><span class="sxs-lookup"><span data-stu-id="394b8-116"> [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)</span></span>
