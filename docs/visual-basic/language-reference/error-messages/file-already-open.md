---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586664"
---
# <a name="file-already-open"></a><span data-ttu-id="02320-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="02320-102">File already open</span></span>
<span data-ttu-id="02320-103">Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="02320-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="02320-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="02320-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="02320-105">Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="02320-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="02320-106">Uma instrução faz referência a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="02320-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02320-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="02320-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="02320-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="02320-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02320-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02320-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
