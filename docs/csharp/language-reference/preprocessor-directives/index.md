---
title: Diretivas de pré-processador do C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 63a7bdb6d36794e0380ca84443926338fe926e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="935c3-102">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="935c3-102">C# preprocessor directives</span></span>
<span data-ttu-id="935c3-103">Esta seção contém informações sobre as seguintes diretivas de pré-processador do C#:</span><span class="sxs-lookup"><span data-stu-id="935c3-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="935c3-104">#if</span><span class="sxs-lookup"><span data-stu-id="935c3-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="935c3-105">#else</span><span class="sxs-lookup"><span data-stu-id="935c3-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="935c3-106">#elif</span><span class="sxs-lookup"><span data-stu-id="935c3-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="935c3-107">#endif</span><span class="sxs-lookup"><span data-stu-id="935c3-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="935c3-108">#define</span><span class="sxs-lookup"><span data-stu-id="935c3-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="935c3-109">#undef</span><span class="sxs-lookup"><span data-stu-id="935c3-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="935c3-110">#warning</span><span class="sxs-lookup"><span data-stu-id="935c3-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="935c3-111">#error</span><span class="sxs-lookup"><span data-stu-id="935c3-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="935c3-112">#line</span><span class="sxs-lookup"><span data-stu-id="935c3-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="935c3-113">#region</span><span class="sxs-lookup"><span data-stu-id="935c3-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="935c3-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="935c3-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="935c3-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="935c3-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="935c3-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="935c3-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="935c3-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="935c3-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="935c3-118">Para obter mais informações e exemplos, consulte os tópicos individuais.</span><span class="sxs-lookup"><span data-stu-id="935c3-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="935c3-119">Embora o compilador não tenha um pré-processador separado, as diretivas descritas nesta seção são processadas como se houvesse um.</span><span class="sxs-lookup"><span data-stu-id="935c3-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="935c3-120">Eles são usados para ajudar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="935c3-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="935c3-121">Ao contrário das diretivas de C e C++, não é possível usar essas diretivas para criar macros.</span><span class="sxs-lookup"><span data-stu-id="935c3-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="935c3-122">Uma diretiva de pré-processador deve ser a única instrução em uma linha.</span><span class="sxs-lookup"><span data-stu-id="935c3-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="935c3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="935c3-123">See also</span></span>
 [<span data-ttu-id="935c3-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="935c3-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="935c3-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="935c3-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
