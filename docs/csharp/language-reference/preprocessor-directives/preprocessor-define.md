---
description: '##define – Referência de C#'
title: '##define – Referência de C#'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 961c20c091a4a6d7da421d94500abd41d2d60a5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160496"
---
# <a name="define-c-reference"></a><span data-ttu-id="1f125-103">#define (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1f125-103">#define (C# Reference)</span></span>

<span data-ttu-id="1f125-104">Use `#define` para definir um símbolo.</span><span class="sxs-lookup"><span data-stu-id="1f125-104">You use `#define` to define a symbol.</span></span> <span data-ttu-id="1f125-105">Quando você usa o símbolo como a expressão passada para a diretiva [#if](./preprocessor-if.md), a expressão será avaliada como `true`, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f125-105">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="1f125-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f125-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f125-107">A diretiva `#define` não pode ser usada para declarar valores constantes como normalmente é feito em C e C++.</span><span class="sxs-lookup"><span data-stu-id="1f125-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="1f125-108">As constantes em C# são mais bem definidas como membros estáticos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="1f125-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="1f125-109">Se você tiver várias dessas constantes, considere criar uma classe "Constantes" separada para guardá-las.</span><span class="sxs-lookup"><span data-stu-id="1f125-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="1f125-110">Os símbolos podem ser usados para especificar condições para compilação.</span><span class="sxs-lookup"><span data-stu-id="1f125-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="1f125-111">É possível testar o símbolo com [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="1f125-111">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="1f125-112">Você também pode usar o <xref:System.Diagnostics.ConditionalAttribute> para executar uma compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="1f125-112">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="1f125-113">É possível definir um símbolo, mas não é possível atribuir um valor a um símbolo.</span><span class="sxs-lookup"><span data-stu-id="1f125-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="1f125-114">A diretiva `#define` deve ser exibida no arquivo antes de usar as instruções que também não são diretivas de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="1f125-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="1f125-115">Você também pode definir um símbolo com a opção [-definir](../compiler-options/define-compiler-option.md) compilador.</span><span class="sxs-lookup"><span data-stu-id="1f125-115">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1f125-116">É possível excluir um símbolo com [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="1f125-116">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="1f125-117">Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="1f125-117">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="1f125-118">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="1f125-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="1f125-119">O escopo de um símbolo criado usando `#define` é o arquivo no qual o símbolo foi definido.</span><span class="sxs-lookup"><span data-stu-id="1f125-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="1f125-120">Como mostra o exemplo a seguir, é necessário colocar as diretivas `#define` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1f125-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="1f125-121">Para obter um exemplo de como excluir um símbolo, consulte [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="1f125-121">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f125-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f125-122">See also</span></span>

- [<span data-ttu-id="1f125-123">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="1f125-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f125-124">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1f125-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f125-125">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="1f125-125">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="1f125-126">const</span><span class="sxs-lookup"><span data-stu-id="1f125-126">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="1f125-127">Como: compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="1f125-127">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="1f125-128">#undef</span><span class="sxs-lookup"><span data-stu-id="1f125-128">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="1f125-129">#if</span><span class="sxs-lookup"><span data-stu-id="1f125-129">#if</span></span>](./preprocessor-if.md)
