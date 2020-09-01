---
description: Diretivas de pré-processador do C#
title: Diretivas de pré-processador do C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: a7ffca8b39f1bd9f05193bccbb6d90e67fa262c9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132359"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="8205e-103">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="8205e-103">C# preprocessor directives</span></span>
<span data-ttu-id="8205e-104">Esta seção contém informações sobre as seguintes diretivas de pré-processador do C#:</span><span class="sxs-lookup"><span data-stu-id="8205e-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="8205e-105">#if</span><span class="sxs-lookup"><span data-stu-id="8205e-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="8205e-106">#else</span><span class="sxs-lookup"><span data-stu-id="8205e-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="8205e-107">#elif</span><span class="sxs-lookup"><span data-stu-id="8205e-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="8205e-108">#endif</span><span class="sxs-lookup"><span data-stu-id="8205e-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="8205e-109">#define</span><span class="sxs-lookup"><span data-stu-id="8205e-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="8205e-110">#undef</span><span class="sxs-lookup"><span data-stu-id="8205e-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="8205e-111">#warning</span><span class="sxs-lookup"><span data-stu-id="8205e-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="8205e-112">#error</span><span class="sxs-lookup"><span data-stu-id="8205e-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="8205e-113">#line</span><span class="sxs-lookup"><span data-stu-id="8205e-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="8205e-114">#region</span><span class="sxs-lookup"><span data-stu-id="8205e-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="8205e-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="8205e-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="8205e-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="8205e-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="8205e-117">aviso de #pragma</span><span class="sxs-lookup"><span data-stu-id="8205e-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="8205e-118">soma de verificação de #pragma</span><span class="sxs-lookup"><span data-stu-id="8205e-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="8205e-119">Para obter mais informações e exemplos, consulte os tópicos individuais.</span><span class="sxs-lookup"><span data-stu-id="8205e-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="8205e-120">Embora o compilador não tenha um pré-processador separado, as diretivas descritas nesta seção são processadas como se houvesse um.</span><span class="sxs-lookup"><span data-stu-id="8205e-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="8205e-121">Eles são usados para ajudar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="8205e-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="8205e-122">Ao contrário das diretivas de C e C++, não é possível usar essas diretivas para criar macros.</span><span class="sxs-lookup"><span data-stu-id="8205e-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="8205e-123">Uma diretiva de pré-processador deve ser a única instrução em uma linha.</span><span class="sxs-lookup"><span data-stu-id="8205e-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="8205e-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="8205e-124">See also</span></span>

- [<span data-ttu-id="8205e-125">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="8205e-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8205e-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8205e-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
