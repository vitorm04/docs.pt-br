---
title: /highentropyva (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ef482f142e07e96eabf93bd2223b0d24f351553b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="fde15-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fde15-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="fde15-103">Indica se um executável de 64 bits ou um executável que está marcado, o [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) opção de compilador dá suporte à alta entropia endereço espaço Layout aleatória (ASLR).</span><span class="sxs-lookup"><span data-stu-id="fde15-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fde15-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fde15-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fde15-105">Arguments</span></span>  
 <span data-ttu-id="fde15-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fde15-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="fde15-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="fde15-107">Optional.</span></span> <span data-ttu-id="fde15-108">A opção está desativada por padrão, ou se você especificar `/highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="fde15-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="fde15-109">A opção está ativada e se você especificar `/highentropyva` ou `/highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="fde15-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fde15-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fde15-110">Remarks</span></span>  
 <span data-ttu-id="fde15-111">Se você especificar essa opção, as versões compatíveis do kernel do Windows podem usar níveis mais altos de entropia ao kernel aleatoriamente o layout do espaço de endereço de um processo como parte da ASLR.</span><span class="sxs-lookup"><span data-stu-id="fde15-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="fde15-112">Se o kernel usa níveis mais altos de entropia, um número maior de endereços pode ser alocado para regiões de memória como pilhas e heaps.</span><span class="sxs-lookup"><span data-stu-id="fde15-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="fde15-113">Como resultado, é mais difícil de adivinhar a localização de uma região específica da memória.</span><span class="sxs-lookup"><span data-stu-id="fde15-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="fde15-114">Quando a opção está ativada, o executável de destino e todos os módulos no qual ele depende deve ser capaz de lidar com valores de ponteiro que são maiores do que 4 gigabytes (GB) quando esses módulos são executados como processos de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fde15-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde15-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fde15-115">See Also</span></span>  
 <span data-ttu-id="fde15-116">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="fde15-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="fde15-117"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="fde15-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
