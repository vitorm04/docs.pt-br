---
title: Número de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 8cbffc7714211fb10bedc3a73729eac59d98f0bb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086979"
---
# <a name="bad-record-number"></a><span data-ttu-id="60926-102">Número de registro inválido</span><span class="sxs-lookup"><span data-stu-id="60926-102">Bad record number</span></span>

<span data-ttu-id="60926-103">O número do registro `a FileGet` na `FilePut` instrução,, `FileGetObject` ou `FilePutObject` é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="60926-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60926-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="60926-104">To correct this error</span></span>  
  
1. <span data-ttu-id="60926-105">Verifique os cálculos usados na geração do número de registro.</span><span class="sxs-lookup"><span data-stu-id="60926-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="60926-106">Verifique a ortografia das variáveis que contêm o número do registro ou usadas no cálculo de números de registro.</span><span class="sxs-lookup"><span data-stu-id="60926-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="60926-107">Um nome de variável digitado incorretamente é declarado implicitamente e inicializado como zero, a menos que você tenha usado `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="60926-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60926-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="60926-108">See also</span></span>

- [<span data-ttu-id="60926-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="60926-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
