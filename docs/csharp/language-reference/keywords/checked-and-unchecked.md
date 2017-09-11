---
title: "Contexto verificado e não verificado (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
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
ms.openlocfilehash: 744f59dbf7ee8370010ff76d4e9dde20490de403
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="808e1-102">Contexto verificado e não verificado (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="808e1-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="808e1-103">Instruções C# podem ser executadas em contexto marcado ou desmarcado.</span><span class="sxs-lookup"><span data-stu-id="808e1-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="808e1-104">Em um contexto marcado, o estouro aritmético gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="808e1-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="808e1-105">Em um contexto desmarcado, o estouro aritmético é ignorado e o resultado é truncado.</span><span class="sxs-lookup"><span data-stu-id="808e1-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="808e1-106">[verificado](../../../csharp/language-reference/keywords/checked.md) Especificar o contexto verificado.</span><span class="sxs-lookup"><span data-stu-id="808e1-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="808e1-107">[não verificado](../../../csharp/language-reference/keywords/unchecked.md) Especificar o contexto não verificado.</span><span class="sxs-lookup"><span data-stu-id="808e1-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="808e1-108">Se nem `checked` nem `unchecked` forem especificados, o contexto padrão dependerá de fatores externos, tais como as opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="808e1-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="808e1-109">As seguintes operações são afetadas pela verificação de estouro:</span><span class="sxs-lookup"><span data-stu-id="808e1-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="808e1-110">Expressões que usam os seguintes operadores predefinidos em tipos integrais:</span><span class="sxs-lookup"><span data-stu-id="808e1-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="808e1-111">`++` `--` – (unário)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="808e1-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="808e1-112">Conversões numéricas explícitas entre tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="808e1-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="808e1-113">A opção do compilador [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) permite especificar contexto verificado ou não verificado para todas as instruções aritméticas de inteiros que não estão explicitamente no escopo de uma palavra-chave `checked` ou `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="808e1-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808e1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="808e1-114">See Also</span></span>  
 <span data-ttu-id="808e1-115">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="808e1-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="808e1-116">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="808e1-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="808e1-117">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="808e1-117">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="808e1-118">Palavras-chave de instrução</span><span class="sxs-lookup"><span data-stu-id="808e1-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)

