---
title: "#<a name=\"if-c-reference\"></a>if (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#if'
dev_langs:
- CSharp
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
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
ms.openlocfilehash: f70dac98d5731370ae961f795b08a71946867d9b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="if-c-reference"></a><span data-ttu-id="fb0bb-102">#if (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fb0bb-102">#if (C# Reference)</span></span>
<span data-ttu-id="fb0bb-103">Quando o compilador C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), ele compilará o código entre as diretivas somente se o símbolo especificado for definido.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="fb0bb-104">Diferentemente do C e do C++, não é possível atribuir um valor numérico a um símbolo; a instrução #if em C# é booliana e testa somente se o símbolo foi definido ou não.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="fb0bb-105">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="fb0bb-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="fb0bb-106">É possível usar os operadores [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (igualdade), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (desigualdade) apenas para testar [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="fb0bb-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="fb0bb-107">True significa que o símbolo foi definido.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-107">True means the symbol is defined.</span></span> <span data-ttu-id="fb0bb-108">A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="fb0bb-109">É possível usar os operadores [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (e), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (ou) e [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb0bb-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="fb0bb-110">(não) para avaliar se vários símbolos foram definidos.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="fb0bb-111">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb0bb-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb0bb-112">Remarks</span></span>  
 <span data-ttu-id="fb0bb-113">`#if`, juntamente com as diretivas [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) e [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md), permite incluir ou excluir código com base na existência de um ou mais símbolos.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="fb0bb-114">Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="fb0bb-115">Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="fb0bb-116">`#define` permite definir um símbolo, de modo que, usando o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="fb0bb-117">Também é possível definir um símbolo com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fb0bb-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="fb0bb-118">É possível excluir um símbolo com [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="fb0bb-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="fb0bb-119">Um símbolo definido com `/define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="fb0bb-120">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="fb0bb-121">O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="fb0bb-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb0bb-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb0bb-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="fb0bb-123">**DEBUG e MYTEST são definidos**</span><span class="sxs-lookup"><span data-stu-id="fb0bb-123">**DEBUG and MYTEST are defined**</span></span>   
## <a name="see-also"></a><span data-ttu-id="fb0bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb0bb-124">See Also</span></span>  
 <span data-ttu-id="fb0bb-125">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb0bb-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fb0bb-126">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb0bb-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="fb0bb-127">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="fb0bb-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

