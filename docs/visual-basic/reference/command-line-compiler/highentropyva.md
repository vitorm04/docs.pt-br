---
title: /highentropyva (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55568808bb94f98ce7a20016fc5a2a0a2ef23a38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="d3615-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3615-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="d3615-103">Indica se um executável de 64 bits ou um executável que é marcado pelo [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) opção de compilador dá suporte à alta entropia endereço espaço Layout aleatória (ASLR).</span><span class="sxs-lookup"><span data-stu-id="d3615-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3615-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3615-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3615-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3615-105">Arguments</span></span>  
 <span data-ttu-id="d3615-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d3615-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d3615-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3615-107">Optional.</span></span> <span data-ttu-id="d3615-108">A opção está desativada por padrão, ou se você especificar `/highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="d3615-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="d3615-109">A opção está ativada e se você especificar `/highentropyva` ou `/highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="d3615-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3615-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3615-110">Remarks</span></span>  
 <span data-ttu-id="d3615-111">Se você especificar essa opção, as versões compatíveis do kernel do Windows podem usar níveis mais altos de entropia ao kernel aleatoriamente o layout do espaço de endereço de um processo como parte de ASLR.</span><span class="sxs-lookup"><span data-stu-id="d3615-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="d3615-112">Se o kernel usa níveis mais altos de entropia, um número maior de endereços pode ser alocado para regiões de memória, como pilhas e heaps.</span><span class="sxs-lookup"><span data-stu-id="d3615-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="d3615-113">Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.</span><span class="sxs-lookup"><span data-stu-id="d3615-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="d3615-114">Quando a opção está ativada, o executável de destino e todos os módulos no qual ele depende deve ser capaz de lidar com valores de ponteiro que são maiores do que 4 gigabytes (GB) quando esses módulos estão sendo executados como processos de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d3615-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3615-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3615-115">See Also</span></span>  
 [<span data-ttu-id="d3615-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3615-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d3615-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3615-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
