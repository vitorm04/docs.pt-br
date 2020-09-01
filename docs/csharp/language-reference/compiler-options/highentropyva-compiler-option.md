---
description: -highentropyva (opções do compilador C#)
title: -highentropyva (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125651"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="c6e0c-103">-highentropyva (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c6e0c-103">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="c6e0c-104">A opção do compilador **-highentropyva** informa ao kernel do Windows se um determinado executável é compatível com ASLR (Address Space Layout Randomization) de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e0c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6e0c-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c6e0c-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c6e0c-106">Arguments</span></span>  
 <span data-ttu-id="c6e0c-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c6e0c-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c6e0c-108">Essa opção especifica que um executável de 64 bits ou um executável que está marcado com a opção do compilador [-platform:anycpu](./platform-compiler-option.md) é compatível com um espaço de endereço virtual de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="c6e0c-109">A opção está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-109">The option is disabled by default.</span></span> <span data-ttu-id="c6e0c-110">Use **-highentropyva+** ou **-highentropyva** para habilitá-la.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6e0c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6e0c-111">Remarks</span></span>  
 <span data-ttu-id="c6e0c-112">A opção **-highentropyva** permite que as versões compatíveis do kernel do Windows usem níveis mais altos de entropia ao randomizar o layout do espaço de endereço de um processo como parte da ASLR.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="c6e0c-113">O uso de níveis mais altos de entropia significa que um número maior de endereços pode ser alocado para regiões de memória como pilhas e heaps.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="c6e0c-114">Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="c6e0c-115">Quando a opção do compilador **-highentropyva** é especificada, o executável de destino e todos os módulos dos quais ele depende devem ser capazes de manipular valores de ponteiro que sejam maiores que 4 GB (gigabytes) quando eles estiverem em execução como um processo de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c6e0c-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
