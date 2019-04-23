---
title: Código e ponteiros não seguros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 3712e04d4496d13178843564b5d0753f62e28fa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678076"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="880ea-102">Código não seguro e ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="880ea-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="880ea-103">Para manter a segurança de tipos e a segurança, o C# não dá suporte à aritmética de ponteiro por padrão.</span><span class="sxs-lookup"><span data-stu-id="880ea-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="880ea-104">No entanto, usando a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md), você pode definir um contexto não seguro no qual os ponteiros podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="880ea-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="880ea-105">Para obter mais informações sobre ponteiros, consulte o tópico [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="880ea-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="880ea-106">No CLR (Common Language Runtime), o código não seguro é conhecido como código não verificado.</span><span class="sxs-lookup"><span data-stu-id="880ea-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="880ea-107">O código não seguro em C# não é necessariamente perigoso. Ele é apenas o código cuja segurança não pode ser verificada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="880ea-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="880ea-108">O CLR, portanto, executará somente o código não seguro se ele estiver em um assembly totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="880ea-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="880ea-109">Se você usar código não seguro, será sua responsabilidade assegurar que seu código não apresente riscos de segurança ou erros de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="880ea-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="880ea-110">Visão Geral de Código Não Seguro</span><span class="sxs-lookup"><span data-stu-id="880ea-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="880ea-111">O código não seguro tem as propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="880ea-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="880ea-112">Blocos de código, tipos e métodos podem ser definidos como não seguros.</span><span class="sxs-lookup"><span data-stu-id="880ea-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="880ea-113">Em alguns casos, o código não seguro pode aumentar o desempenho de um aplicativo removendo as verificações de limites de matriz.</span><span class="sxs-lookup"><span data-stu-id="880ea-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="880ea-114">O código não seguro é necessário quando você chama funções nativas que exigem ponteiros.</span><span class="sxs-lookup"><span data-stu-id="880ea-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="880ea-115">Usar o código não seguro apresenta riscos de segurança e estabilidade.</span><span class="sxs-lookup"><span data-stu-id="880ea-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="880ea-116">Para que o C# compile o código não seguro, o aplicativo deve ser compilado com [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="880ea-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="880ea-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="880ea-117">Related Sections</span></span>  
 <span data-ttu-id="880ea-118">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="880ea-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="880ea-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="880ea-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="880ea-120">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="880ea-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="880ea-121">Como: usar ponteiros para copiar uma matriz de bytes</span><span class="sxs-lookup"><span data-stu-id="880ea-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="880ea-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="880ea-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="880ea-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="880ea-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="880ea-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="880ea-124">See also</span></span>

- [<span data-ttu-id="880ea-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="880ea-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
