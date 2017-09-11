---
title: "Número de registro incorreto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ec302a6093cd352367e499ca3e40ff796fdb8f2b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-record-number"></a><span data-ttu-id="e6c7e-102">Número de registro incorreto</span><span class="sxs-lookup"><span data-stu-id="e6c7e-102">Bad record number</span></span>
<span data-ttu-id="e6c7e-103">O número do registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="e6c7e-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e6c7e-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e6c7e-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="e6c7e-105">Verifique os cálculos usados na geração de número de registro.</span><span class="sxs-lookup"><span data-stu-id="e6c7e-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="e6c7e-106">Verifique se as variáveis contendo o número de registro ou usado para calcular números de registro.</span><span class="sxs-lookup"><span data-stu-id="e6c7e-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="e6c7e-107">Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.</span><span class="sxs-lookup"><span data-stu-id="e6c7e-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c7e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6c7e-108">See Also</span></span>  
 [<span data-ttu-id="e6c7e-109">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="e6c7e-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
