---
title: Número de registro incorreto
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-record-number"></a><span data-ttu-id="d3f45-102">Número de registro incorreto</span><span class="sxs-lookup"><span data-stu-id="d3f45-102">Bad record number</span></span>
<span data-ttu-id="d3f45-103">O número do registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="d3f45-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3f45-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d3f45-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="d3f45-105">Verifique os cálculos usados para gerar o número do registro.</span><span class="sxs-lookup"><span data-stu-id="d3f45-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="d3f45-106">Verifique se as variáveis que contém o número de registro ou usada no cálculo de números de registro.</span><span class="sxs-lookup"><span data-stu-id="d3f45-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="d3f45-107">Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="d3f45-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f45-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3f45-108">See Also</span></span>  
 [<span data-ttu-id="d3f45-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="d3f45-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
