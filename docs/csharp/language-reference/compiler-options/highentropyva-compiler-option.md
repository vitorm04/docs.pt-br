---
title: -highentropyva (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606852"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="996a1-102">-highentropyva (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="996a1-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="996a1-103">A opção do compilador **-highentropyva** informa ao kernel do Windows se um determinado executável é compatível com ASLR (Address Space Layout Randomization) de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="996a1-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="996a1-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="996a1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="996a1-105">Arguments</span></span>  
 <span data-ttu-id="996a1-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="996a1-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="996a1-107">Essa opção especifica que um executável de 64 bits ou um executável que está marcado com a opção do compilador [-platform:anycpu](./platform-compiler-option.md) é compatível com um espaço de endereço virtual de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="996a1-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="996a1-108">A opção está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="996a1-108">The option is disabled by default.</span></span> <span data-ttu-id="996a1-109">Use **-highentropyva+** ou **-highentropyva** para habilitá-la.</span><span class="sxs-lookup"><span data-stu-id="996a1-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996a1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="996a1-110">Remarks</span></span>  
 <span data-ttu-id="996a1-111">A opção **-highentropyva** permite que as versões compatíveis do kernel do Windows usem níveis mais altos de entropia ao randomizar o layout do espaço de endereço de um processo como parte da ASLR.</span><span class="sxs-lookup"><span data-stu-id="996a1-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="996a1-112">O uso de níveis mais altos de entropia significa que um número maior de endereços pode ser alocado para regiões de memória como pilhas e heaps.</span><span class="sxs-lookup"><span data-stu-id="996a1-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="996a1-113">Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.</span><span class="sxs-lookup"><span data-stu-id="996a1-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="996a1-114">Quando a opção do compilador **-highentropyva** é especificada, o executável de destino e todos os módulos dos quais ele depende devem ser capazes de manipular valores de ponteiro que sejam maiores que 4 GB (gigabytes) quando eles estiverem em execução como um processo de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="996a1-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
