---
title: Número de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: fbf1a2db97d0474fb758ff5ed572e94395a187da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664741"
---
# <a name="bad-record-number"></a><span data-ttu-id="a99aa-102">Número de registro inválido</span><span class="sxs-lookup"><span data-stu-id="a99aa-102">Bad record number</span></span>
<span data-ttu-id="a99aa-103">O número de registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="a99aa-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a99aa-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a99aa-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a99aa-105">Verifique os cálculos usados para gerar o número do registro.</span><span class="sxs-lookup"><span data-stu-id="a99aa-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="a99aa-106">Verifique a ortografia das variáveis que contém o número de registro ou usado no cálculo de números de registro.</span><span class="sxs-lookup"><span data-stu-id="a99aa-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="a99aa-107">Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="a99aa-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99aa-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a99aa-108">See also</span></span>
- [<span data-ttu-id="a99aa-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a99aa-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
