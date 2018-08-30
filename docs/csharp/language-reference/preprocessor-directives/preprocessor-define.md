---
title: '#define (Referência de C#)'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 305d52c26fb2592874d06f2c9a75ec63b472a812
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933058"
---
# <a name="define-c-reference"></a><span data-ttu-id="b7b41-102">#define (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b7b41-102">#define (C# Reference)</span></span>
<span data-ttu-id="b7b41-103">Use `#define` para definir um símbolo.</span><span class="sxs-lookup"><span data-stu-id="b7b41-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="b7b41-104">Quando você usa o símbolo como a expressão passada para a diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `true`, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b7b41-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="b7b41-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7b41-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7b41-106">A diretiva `#define` não pode ser usada para declarar valores constantes como normalmente é feito em C e C++.</span><span class="sxs-lookup"><span data-stu-id="b7b41-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="b7b41-107">As constantes em C# são mais bem definidas como membros estáticos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="b7b41-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="b7b41-108">Se você tiver várias dessas constantes, considere criar uma classe "Constantes" separada para guardá-las.</span><span class="sxs-lookup"><span data-stu-id="b7b41-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="b7b41-109">Os símbolos podem ser usados para especificar condições para compilação.</span><span class="sxs-lookup"><span data-stu-id="b7b41-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="b7b41-110">É possível testar o símbolo com [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="b7b41-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="b7b41-111">Você também pode usar o <xref:System.Diagnostics.ConditionalAttribute> para executar uma compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="b7b41-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="b7b41-112">É possível definir um símbolo, mas não é possível atribuir um valor a um símbolo.</span><span class="sxs-lookup"><span data-stu-id="b7b41-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="b7b41-113">A diretiva `#define` deve ser exibida no arquivo antes de usar as instruções que também não são diretivas de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="b7b41-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="b7b41-114">Você também pode definir um símbolo com a opção do compilador [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b7b41-114">You can also define a symbol with the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b7b41-115">É possível excluir um símbolo com [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="b7b41-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="b7b41-116">Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="b7b41-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="b7b41-117">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="b7b41-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="b7b41-118">O escopo de um símbolo criado usando `#define` é o arquivo no qual o símbolo foi definido.</span><span class="sxs-lookup"><span data-stu-id="b7b41-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="b7b41-119">Como mostra o exemplo a seguir, é necessário colocar as diretivas `#define` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="b7b41-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="b7b41-120">Para obter um exemplo de como excluir um símbolo, consulte [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="b7b41-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b41-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7b41-121">See Also</span></span>

- [<span data-ttu-id="b7b41-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b7b41-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b7b41-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b7b41-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b7b41-124">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b7b41-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="b7b41-125">const</span><span class="sxs-lookup"><span data-stu-id="b7b41-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
- [<span data-ttu-id="b7b41-126">Como compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="b7b41-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
- [<span data-ttu-id="b7b41-127">#undef</span><span class="sxs-lookup"><span data-stu-id="b7b41-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
- [<span data-ttu-id="b7b41-128">#if</span><span class="sxs-lookup"><span data-stu-id="b7b41-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
