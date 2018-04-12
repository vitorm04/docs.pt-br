---
title: Arquivo já aberto
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="d753e-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="d753e-102">File already open</span></span>
<span data-ttu-id="d753e-103">Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="d753e-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="d753e-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="d753e-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="d753e-105">Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="d753e-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="d753e-106">Uma instrução faz referência a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="d753e-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d753e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d753e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="d753e-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="d753e-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d753e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d753e-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
