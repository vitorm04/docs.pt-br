---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344247"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="e5a86-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5a86-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="e5a86-103">Indica se um executável de 64 bits ou um executável que é marcado pela opção de compilador [-Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) dá suporte à alta possibilidade de seleção de layout de espaço de endereço de entropia (ASLR).</span><span class="sxs-lookup"><span data-stu-id="e5a86-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5a86-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5a86-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e5a86-105">Arguments</span></span>  
 <span data-ttu-id="e5a86-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e5a86-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e5a86-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e5a86-107">Optional.</span></span> <span data-ttu-id="e5a86-108">A opção está desativada por padrão ou, `-highentropyva-`se você especificar.</span><span class="sxs-lookup"><span data-stu-id="e5a86-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="e5a86-109">A opção estará ativada se você `-highentropyva` especificar `-highentropyva+`ou.</span><span class="sxs-lookup"><span data-stu-id="e5a86-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a86-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5a86-110">Remarks</span></span>  
 <span data-ttu-id="e5a86-111">Se você especificar essa opção, as versões compatíveis do kernel do Windows poderão usar graus mais altos de entropia quando o kernel distribui o layout de espaço de endereço de um processo como parte de ASLR.</span><span class="sxs-lookup"><span data-stu-id="e5a86-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="e5a86-112">Se o kernel usar graus maiores de entropia, um número maior de endereços poderá ser alocado para regiões de memória, como pilhas e heaps.</span><span class="sxs-lookup"><span data-stu-id="e5a86-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="e5a86-113">Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.</span><span class="sxs-lookup"><span data-stu-id="e5a86-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="e5a86-114">Quando a opção está ativada, o executável de destino e todos os módulos dos quais depende devem ser capazes de lidar com valores de ponteiro maiores que 4 gigabytes (GB) quando esses módulos estiverem sendo executados como processos de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e5a86-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a86-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="e5a86-115">See also</span></span>

- [<span data-ttu-id="e5a86-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5a86-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e5a86-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5a86-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
