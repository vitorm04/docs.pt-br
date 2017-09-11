---
title: "Diretivas de pré-processador em C#"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.preprocessor
dev_langs:
- CSharp
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91bb2daefbc677fad8a3dd93b37aac996234d48c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="bb22b-102">Diretivas de pré-processador em C#</span><span class="sxs-lookup"><span data-stu-id="bb22b-102">C# Preprocessor Directives</span></span>
<span data-ttu-id="bb22b-103">Esta seção contém informações sobre as seguintes diretivas de pré-processador de C#.</span><span class="sxs-lookup"><span data-stu-id="bb22b-103">This section contains information about the following C# preprocessor directives.</span></span>  
  
 [<span data-ttu-id="bb22b-104">#if</span><span class="sxs-lookup"><span data-stu-id="bb22b-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)  
  
 [<span data-ttu-id="bb22b-105">#else</span><span class="sxs-lookup"><span data-stu-id="bb22b-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)  
  
 [<span data-ttu-id="bb22b-106">#elif</span><span class="sxs-lookup"><span data-stu-id="bb22b-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)  
  
 [<span data-ttu-id="bb22b-107">#endif</span><span class="sxs-lookup"><span data-stu-id="bb22b-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)  
  
 [<span data-ttu-id="bb22b-108">#define</span><span class="sxs-lookup"><span data-stu-id="bb22b-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)  
  
 [<span data-ttu-id="bb22b-109">#undef</span><span class="sxs-lookup"><span data-stu-id="bb22b-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
  
 [<span data-ttu-id="bb22b-110">#warning</span><span class="sxs-lookup"><span data-stu-id="bb22b-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)  
  
 [<span data-ttu-id="bb22b-111">#error</span><span class="sxs-lookup"><span data-stu-id="bb22b-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)  
  
 [<span data-ttu-id="bb22b-112">#line</span><span class="sxs-lookup"><span data-stu-id="bb22b-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)  
  
 [<span data-ttu-id="bb22b-113">#region</span><span class="sxs-lookup"><span data-stu-id="bb22b-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)  
  
 [<span data-ttu-id="bb22b-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="bb22b-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)  
  
 [<span data-ttu-id="bb22b-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="bb22b-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)  
  
 [<span data-ttu-id="bb22b-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="bb22b-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="bb22b-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="bb22b-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
 <span data-ttu-id="bb22b-118">Para obter mais informações e exemplos, consulte os tópicos individuais.</span><span class="sxs-lookup"><span data-stu-id="bb22b-118">See the individual topics for more information and examples.</span></span>  
  
 <span data-ttu-id="bb22b-119">Embora o compilador não tenha um pré-processador separado, as diretivas descritas nesta seção são processadas como se houvesse um.</span><span class="sxs-lookup"><span data-stu-id="bb22b-119">Although the compiler does not have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="bb22b-120">Eles são usados para ajudar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="bb22b-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="bb22b-121">Ao contrário das diretivas de C e C++, não é possível usar essas diretivas para criar macros.</span><span class="sxs-lookup"><span data-stu-id="bb22b-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>  
  
 <span data-ttu-id="bb22b-122">Uma diretiva de pré-processador deve ser a única instrução em uma linha.</span><span class="sxs-lookup"><span data-stu-id="bb22b-122">A preprocessor directive must be the only instruction on a line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb22b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb22b-123">See Also</span></span>  
 <span data-ttu-id="bb22b-124">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb22b-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="bb22b-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bb22b-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

