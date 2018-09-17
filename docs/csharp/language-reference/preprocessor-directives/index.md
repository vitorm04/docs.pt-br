---
title: Diretivas de pré-processador do C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1c0a97cabce347be0bc9367f3d090a1fc699db19
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45694162"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="40bf8-102">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="40bf8-102">C# preprocessor directives</span></span>
<span data-ttu-id="40bf8-103">Esta seção contém informações sobre as seguintes diretivas de pré-processador do C#:</span><span class="sxs-lookup"><span data-stu-id="40bf8-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="40bf8-104">#if</span><span class="sxs-lookup"><span data-stu-id="40bf8-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="40bf8-105">#else</span><span class="sxs-lookup"><span data-stu-id="40bf8-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="40bf8-106">#elif</span><span class="sxs-lookup"><span data-stu-id="40bf8-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="40bf8-107">#endif</span><span class="sxs-lookup"><span data-stu-id="40bf8-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="40bf8-108">#define</span><span class="sxs-lookup"><span data-stu-id="40bf8-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="40bf8-109">#undef</span><span class="sxs-lookup"><span data-stu-id="40bf8-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="40bf8-110">#warning</span><span class="sxs-lookup"><span data-stu-id="40bf8-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="40bf8-111">#error</span><span class="sxs-lookup"><span data-stu-id="40bf8-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="40bf8-112">#line</span><span class="sxs-lookup"><span data-stu-id="40bf8-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="40bf8-113">#region</span><span class="sxs-lookup"><span data-stu-id="40bf8-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="40bf8-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="40bf8-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="40bf8-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="40bf8-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="40bf8-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="40bf8-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="40bf8-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="40bf8-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="40bf8-118">Para obter mais informações e exemplos, consulte os tópicos individuais.</span><span class="sxs-lookup"><span data-stu-id="40bf8-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="40bf8-119">Embora o compilador não tenha um pré-processador separado, as diretivas descritas nesta seção são processadas como se houvesse um.</span><span class="sxs-lookup"><span data-stu-id="40bf8-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="40bf8-120">Eles são usados para ajudar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="40bf8-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="40bf8-121">Ao contrário das diretivas de C e C++, não é possível usar essas diretivas para criar macros.</span><span class="sxs-lookup"><span data-stu-id="40bf8-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="40bf8-122">Uma diretiva de pré-processador deve ser a única instrução em uma linha.</span><span class="sxs-lookup"><span data-stu-id="40bf8-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="40bf8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40bf8-123">See also</span></span>

- [<span data-ttu-id="40bf8-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="40bf8-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="40bf8-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="40bf8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
