---
title: Não é possível gravar no arquivo de log porque a gravação para ele reduziria o espaço em disco livre abaixo do valor de ReservedSpace
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: 30c2f90d1c5e03db4ffc289ad3a1a6bc9f7fa689
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58026481"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="852d3-102">Não é possível gravar no arquivo de log porque a gravação para ele reduziria o espaço em disco livre abaixo do valor de ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="852d3-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="852d3-103">O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde gravar o arquivo de log porque:</span><span class="sxs-lookup"><span data-stu-id="852d3-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="852d3-104">A quantidade de espaço livre em disco (em bytes) é menor que o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="852d3-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="852d3-105">— e —</span><span class="sxs-lookup"><span data-stu-id="852d3-105">—and—</span></span>  
  
-   <span data-ttu-id="852d3-106">O valor de <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade era <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="852d3-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="852d3-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="852d3-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="852d3-108">Arquive os logs existentes e remova-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.</span><span class="sxs-lookup"><span data-stu-id="852d3-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="852d3-109">Altere o valor da <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> propriedade para um número menor para reservar menos espaço em disco.</span><span class="sxs-lookup"><span data-stu-id="852d3-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3.  <span data-ttu-id="852d3-110">Defina as <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> propriedade para <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> para descartar as mensagens sem aviso se não houver espaço livre em disco.</span><span class="sxs-lookup"><span data-stu-id="852d3-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852d3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="852d3-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="852d3-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="852d3-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="852d3-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="852d3-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
