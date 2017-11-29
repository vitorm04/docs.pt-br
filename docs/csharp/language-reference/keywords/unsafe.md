---
title: "unsafe (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords: unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="c454a-102">unsafe (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c454a-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="c454a-103">A palavra-chave `unsafe` denota um contexto inseguro, que é necessário para qualquer operação que envolva ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c454a-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="c454a-104">Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c454a-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="c454a-105">Você pode usar o modificador `unsafe` na declaração de um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="c454a-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="c454a-106">Toda a extensão textual do tipo ou membro é, portanto, considerada um contexto inseguro.</span><span class="sxs-lookup"><span data-stu-id="c454a-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="c454a-107">Por exemplo, a seguir está um método declarado com o modificador `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="c454a-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="c454a-108">O escopo do contexto inseguro se estende da lista de parâmetros até o final do método, portanto, os ponteiros também podem ser usados na lista de parâmetros:</span><span class="sxs-lookup"><span data-stu-id="c454a-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="c454a-109">Você também pode usar um bloco não seguro para habilitar o uso de um código não seguro dentro desse bloco.</span><span class="sxs-lookup"><span data-stu-id="c454a-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="c454a-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c454a-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="c454a-111">Para compilar o código não seguro, você deve especificar a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c454a-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c454a-112">O código não seguro não é verificável pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c454a-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c454a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c454a-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c454a-114">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c454a-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c454a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c454a-115">See Also</span></span>  
 [<span data-ttu-id="c454a-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c454a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c454a-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c454a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c454a-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c454a-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c454a-119">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="c454a-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="c454a-120">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="c454a-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="c454a-121">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="c454a-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
