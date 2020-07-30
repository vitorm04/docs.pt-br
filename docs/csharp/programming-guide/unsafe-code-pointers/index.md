---
title: Código e ponteiros não seguros – Guia de Programação em C#
Description: Saiba mais sobre códigos e ponteiros sem segurança. O C# não dá suporte a ponteiros, mas você pode definir um contexto não seguro no qual os ponteiros podem ser usados com uma palavra-chave ' unsafe '.
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
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381769"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="fa0c4-104">Código e ponteiros não seguros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fa0c4-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="fa0c4-105">Para manter a segurança de tipos e a segurança, o C# não dá suporte à aritmética de ponteiro por padrão.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="fa0c4-106">No entanto, usando a palavra-chave [unsafe](../../language-reference/keywords/unsafe.md), você pode definir um contexto não seguro no qual os ponteiros podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="fa0c4-107">Para obter mais informações sobre ponteiros, confira [Tipos de ponteiro](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="fa0c4-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa0c4-108">No CLR (Common Language Runtime), o código não seguro é conhecido como código não verificado.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="fa0c4-109">O código não seguro em C# não é necessariamente perigoso. Ele é apenas o código cuja segurança não pode ser verificada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="fa0c4-110">O CLR, portanto, executará somente o código não seguro se ele estiver em um assembly totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="fa0c4-111">Se você usar código não seguro, será sua responsabilidade assegurar que seu código não apresente riscos de segurança ou erros de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="fa0c4-112">Visão Geral de código não seguro</span><span class="sxs-lookup"><span data-stu-id="fa0c4-112">Unsafe code overview</span></span>

<span data-ttu-id="fa0c4-113">O código não seguro tem as propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa0c4-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="fa0c4-114">Blocos de código, tipos e métodos podem ser definidos como não seguros.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="fa0c4-115">Em alguns casos, o código não seguro pode aumentar o desempenho de um aplicativo removendo as verificações de limites de matriz.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="fa0c4-116">O código não seguro é necessário quando você chama funções nativas que exigem ponteiros.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="fa0c4-117">Usar o código não seguro apresenta riscos de segurança e estabilidade.</span><span class="sxs-lookup"><span data-stu-id="fa0c4-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="fa0c4-118">O código que contém blocos não seguros deve ser compilado com a opção do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fa0c4-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="fa0c4-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="fa0c4-119">Related sections</span></span>

<span data-ttu-id="fa0c4-120">Para obter mais informações, veja:</span><span class="sxs-lookup"><span data-stu-id="fa0c4-120">For more information, see:</span></span>

- [<span data-ttu-id="fa0c4-121">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="fa0c4-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="fa0c4-122">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="fa0c4-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="fa0c4-123">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fa0c4-123">C# language specification</span></span>

<span data-ttu-id="fa0c4-124">Para obter mais informações, confira o tópico [Código não seguro](~/_csharplang/spec/unsafe-code.md) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="fa0c4-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fa0c4-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="fa0c4-125">See also</span></span>

- [<span data-ttu-id="fa0c4-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="fa0c4-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa0c4-127">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="fa0c4-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
