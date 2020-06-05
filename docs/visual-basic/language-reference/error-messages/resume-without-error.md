---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400364"
---
# <a name="resume-without-error"></a><span data-ttu-id="eced4-102">Retomar sem erro</span><span class="sxs-lookup"><span data-stu-id="eced4-102">Resume without error</span></span>
<span data-ttu-id="eced4-103">Uma `Resume` instrução apareceu fora do código de tratamento de erros ou o código entrou em um manipulador de erros, embora não haja erro.</span><span class="sxs-lookup"><span data-stu-id="eced4-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eced4-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eced4-104">To correct this error</span></span>  
  
1. <span data-ttu-id="eced4-105">Mova a `Resume` instrução para um manipulador de erro ou exclua-a.</span><span class="sxs-lookup"><span data-stu-id="eced4-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="eced4-106">Saltos para rótulos não podem ocorrer entre procedimentos. portanto, pesquise o procedimento para o rótulo que identifica o manipulador de erros.</span><span class="sxs-lookup"><span data-stu-id="eced4-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="eced4-107">Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é uma `On Error GoTo` instrução, altere o rótulo da linha para concordar com o destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="eced4-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eced4-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="eced4-108">See also</span></span>

- [<span data-ttu-id="eced4-109">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="eced4-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="eced4-110">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="eced4-110">On Error Statement</span></span>](../statements/on-error-statement.md)
