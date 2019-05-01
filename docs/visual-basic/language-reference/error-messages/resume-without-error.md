---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 61332486b20af66af24eac06b222a38353578c16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055154"
---
# <a name="resume-without-error"></a><span data-ttu-id="752b6-102">Retomar sem erro</span><span class="sxs-lookup"><span data-stu-id="752b6-102">Resume without error</span></span>
<span data-ttu-id="752b6-103">Um `Resume` instrução apareceu fora do código de tratamento de erro ou o código entrou em um manipulador de erro, mesmo que não houve erro.</span><span class="sxs-lookup"><span data-stu-id="752b6-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="752b6-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="752b6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="752b6-105">Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="752b6-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="752b6-106">Portanto, salta para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="752b6-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="752b6-107">Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não seja um `On Error GoTo` instrução, altere o rótulo de linha de acordo com seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="752b6-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752b6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="752b6-108">See also</span></span>

- [<span data-ttu-id="752b6-109">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="752b6-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="752b6-110">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="752b6-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
