---
title: Número de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340796"
---
# <a name="bad-record-number"></a><span data-ttu-id="b30d2-102">Número de registro inválido</span><span class="sxs-lookup"><span data-stu-id="b30d2-102">Bad record number</span></span>
<span data-ttu-id="b30d2-103">O número de registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="b30d2-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b30d2-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b30d2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b30d2-105">Verifique os cálculos usados para gerar o número do registro.</span><span class="sxs-lookup"><span data-stu-id="b30d2-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="b30d2-106">Verifique a ortografia das variáveis que contém o número de registro ou usado no cálculo de números de registro.</span><span class="sxs-lookup"><span data-stu-id="b30d2-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="b30d2-107">Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="b30d2-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30d2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b30d2-108">See also</span></span>

- [<span data-ttu-id="b30d2-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="b30d2-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
