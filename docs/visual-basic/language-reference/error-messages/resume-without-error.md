---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 55295997e5e534b091063815d5ad1a37b81638ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686615"
---
# <a name="resume-without-error"></a><span data-ttu-id="27bc2-102">Retomar sem erro</span><span class="sxs-lookup"><span data-stu-id="27bc2-102">Resume without error</span></span>
<span data-ttu-id="27bc2-103">Um `Resume` instrução apareceu fora do código de tratamento de erro ou o código entrou em um manipulador de erro, mesmo que não houve erro.</span><span class="sxs-lookup"><span data-stu-id="27bc2-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27bc2-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="27bc2-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="27bc2-105">Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="27bc2-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="27bc2-106">Portanto, salta para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="27bc2-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="27bc2-107">Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não seja um `On Error GoTo` instrução, altere o rótulo de linha de acordo com seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="27bc2-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bc2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27bc2-108">See also</span></span>
- [<span data-ttu-id="27bc2-109">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="27bc2-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="27bc2-110">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="27bc2-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
