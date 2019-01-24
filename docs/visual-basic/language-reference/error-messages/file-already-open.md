---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: cda72e03eb5c2469b8106957a0c50fbfa5314549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567029"
---
# <a name="file-already-open"></a><span data-ttu-id="60564-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="60564-102">File already open</span></span>
<span data-ttu-id="60564-103">Às vezes, um arquivo deve ser fechado antes da outra `FileOpen` ou outra operação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="60564-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="60564-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="60564-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="60564-105">Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="60564-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="60564-106">Uma declaração se refere a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="60564-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60564-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="60564-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="60564-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="60564-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60564-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60564-109">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
