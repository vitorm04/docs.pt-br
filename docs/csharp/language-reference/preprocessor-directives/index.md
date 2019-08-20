---
title: Diretivas de pré-processador do C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: f63ba3e0bd89a88ad04b14c2f359a8cde65e8f12
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608606"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="aa5bb-102">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="aa5bb-102">C# preprocessor directives</span></span>
<span data-ttu-id="aa5bb-103">Esta seção contém informações sobre as seguintes diretivas de pré-processador do C#:</span><span class="sxs-lookup"><span data-stu-id="aa5bb-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="aa5bb-104">#if</span><span class="sxs-lookup"><span data-stu-id="aa5bb-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="aa5bb-105">#else</span><span class="sxs-lookup"><span data-stu-id="aa5bb-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="aa5bb-106">#elif</span><span class="sxs-lookup"><span data-stu-id="aa5bb-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="aa5bb-107">#endif</span><span class="sxs-lookup"><span data-stu-id="aa5bb-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="aa5bb-108">#define</span><span class="sxs-lookup"><span data-stu-id="aa5bb-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="aa5bb-109">#undef</span><span class="sxs-lookup"><span data-stu-id="aa5bb-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="aa5bb-110">#warning</span><span class="sxs-lookup"><span data-stu-id="aa5bb-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="aa5bb-111">#error</span><span class="sxs-lookup"><span data-stu-id="aa5bb-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="aa5bb-112">#line</span><span class="sxs-lookup"><span data-stu-id="aa5bb-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="aa5bb-113">#region</span><span class="sxs-lookup"><span data-stu-id="aa5bb-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="aa5bb-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="aa5bb-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="aa5bb-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="aa5bb-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="aa5bb-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="aa5bb-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="aa5bb-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="aa5bb-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="aa5bb-118">Para obter mais informações e exemplos, consulte os tópicos individuais.</span><span class="sxs-lookup"><span data-stu-id="aa5bb-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="aa5bb-119">Embora o compilador não tenha um pré-processador separado, as diretivas descritas nesta seção são processadas como se houvesse um.</span><span class="sxs-lookup"><span data-stu-id="aa5bb-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="aa5bb-120">Eles são usados para ajudar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="aa5bb-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="aa5bb-121">Ao contrário das diretivas de C e C++, não é possível usar essas diretivas para criar macros.</span><span class="sxs-lookup"><span data-stu-id="aa5bb-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="aa5bb-122">Uma diretiva de pré-processador deve ser a única instrução em uma linha.</span><span class="sxs-lookup"><span data-stu-id="aa5bb-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa5bb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa5bb-123">See also</span></span>

- [<span data-ttu-id="aa5bb-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="aa5bb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa5bb-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aa5bb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
