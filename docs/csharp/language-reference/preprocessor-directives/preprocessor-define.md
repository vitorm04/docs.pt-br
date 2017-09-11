---
title: "#<a name=\"define-c-reference\"></a>define (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
dev_langs:
- CSharp
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
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
ms.openlocfilehash: 8ace15f79480c9aeb0fcb4c7d46c207d4904cef0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="define-c-reference"></a><span data-ttu-id="4b64a-102">#define (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4b64a-102">#define (C# Reference)</span></span>
<span data-ttu-id="4b64a-103">Use `#define` para definir um símbolo.</span><span class="sxs-lookup"><span data-stu-id="4b64a-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="4b64a-104">Quando você usa o símbolo como a expressão passada para a diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `true`, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b64a-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
  
 <span data-ttu-id="4b64a-105">`#`  `define`   `DEBUG`</span><span class="sxs-lookup"><span data-stu-id="4b64a-105">`#`  `define`   `DEBUG`</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b64a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b64a-106">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b64a-107">A diretiva `#define` não pode ser usada para declarar valores constantes como normalmente é feito em C e C++.</span><span class="sxs-lookup"><span data-stu-id="4b64a-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="4b64a-108">As constantes em C# são mais bem definidas como membros estáticos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="4b64a-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="4b64a-109">Se você tiver várias dessas constantes, considere criar uma classe "Constantes" separada para guardá-las.</span><span class="sxs-lookup"><span data-stu-id="4b64a-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="4b64a-110">Os símbolos podem ser usados para especificar condições para compilação.</span><span class="sxs-lookup"><span data-stu-id="4b64a-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="4b64a-111">É possível testar o símbolo com [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="4b64a-111">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="4b64a-112">Também é possível usar o atributo `conditional` para executar a compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="4b64a-112">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="4b64a-113">É possível definir um símbolo, mas não é possível atribuir um valor a um símbolo.</span><span class="sxs-lookup"><span data-stu-id="4b64a-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="4b64a-114">A diretiva `#define` deve ser exibida no arquivo antes de usar as instruções que também não são diretivas de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="4b64a-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="4b64a-115">Também é possível definir um símbolo com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4b64a-115">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="4b64a-116">É possível excluir um símbolo com [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="4b64a-116">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="4b64a-117">Um símbolo definido com `/define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4b64a-117">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="4b64a-118">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="4b64a-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="4b64a-119">O escopo de um símbolo criado usando `#define` é o arquivo no qual o símbolo foi definido.</span><span class="sxs-lookup"><span data-stu-id="4b64a-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="4b64a-120">Como mostra o exemplo a seguir, é necessário colocar as diretivas `#define` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4b64a-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="4b64a-121">Para obter um exemplo de como excluir um símbolo, consulte [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="4b64a-121">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b64a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b64a-122">See Also</span></span>  
 <span data-ttu-id="4b64a-123">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4b64a-124">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4b64a-125">[Diretivas de pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-125">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="4b64a-126">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-126">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 <span data-ttu-id="4b64a-127">[Como compilar condicionalmente com Trace e Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-127">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span></span>  
 <span data-ttu-id="4b64a-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span><span class="sxs-lookup"><span data-stu-id="4b64a-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span></span>  
 [<span data-ttu-id="4b64a-129">#if</span><span class="sxs-lookup"><span data-stu-id="4b64a-129">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)

