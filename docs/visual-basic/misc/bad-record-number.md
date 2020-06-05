---
title: Número de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367536"
---
# <a name="bad-record-number"></a><span data-ttu-id="caf58-102">Número de registro inválido</span><span class="sxs-lookup"><span data-stu-id="caf58-102">Bad record number</span></span>
<span data-ttu-id="caf58-103">O número do registro `a FileGet` na `FilePut` instrução,, `FileGetObject` ou `FilePutObject` é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="caf58-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="caf58-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="caf58-104">To correct this error</span></span>  
  
1. <span data-ttu-id="caf58-105">Verifique os cálculos usados na geração do número de registro.</span><span class="sxs-lookup"><span data-stu-id="caf58-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="caf58-106">Verifique a ortografia das variáveis que contêm o número do registro ou usadas no cálculo de números de registro.</span><span class="sxs-lookup"><span data-stu-id="caf58-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="caf58-107">Um nome de variável digitado incorretamente é declarado implicitamente e inicializado como zero, a menos que você tenha usado `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="caf58-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf58-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="caf58-108">See also</span></span>

- [<span data-ttu-id="caf58-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="caf58-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
