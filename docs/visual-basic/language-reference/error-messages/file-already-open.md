---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301315"
---
# <a name="file-already-open"></a><span data-ttu-id="c19cc-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="c19cc-102">File already open</span></span>
<span data-ttu-id="c19cc-103">Às vezes, um arquivo deve ser fechado antes da outra `FileOpen` ou outra operação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="c19cc-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="c19cc-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="c19cc-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="c19cc-105">Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="c19cc-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="c19cc-106">Uma declaração se refere a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="c19cc-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c19cc-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c19cc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="c19cc-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="c19cc-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19cc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c19cc-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
