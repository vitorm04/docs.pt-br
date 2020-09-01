---
description: Palavra-chave protected – Referência de C#
title: Palavra-chave protected – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 4c18d1f2f45a0a154dccd42736a01874dd1af853
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122375"
---
# <a name="protected-c-reference"></a><span data-ttu-id="89815-103">protected (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="89815-103">protected (C# Reference)</span></span>

<span data-ttu-id="89815-104">A palavra-chave `protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="89815-104">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="89815-105">Esta página aborda o acesso `protected`.</span><span class="sxs-lookup"><span data-stu-id="89815-105">This page covers `protected` access.</span></span> <span data-ttu-id="89815-106">A `protected` palavra-chave também faz parte [`protected internal`](protected-internal.md) dos [`private protected`](private-protected.md) modificadores de acesso e.</span><span class="sxs-lookup"><span data-stu-id="89815-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="89815-107">Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="89815-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="89815-108">Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="89815-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="89815-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89815-109">Example</span></span>

<span data-ttu-id="89815-110">Um membro protegido de uma classe base será acessível em uma classe derivada somente se o acesso ocorrer por meio do tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="89815-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="89815-111">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="89815-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="89815-112">A instrução `a.x = 10` gera um erro porque ela é feita dentro do método estático Main e não em uma instância da classe B.</span><span class="sxs-lookup"><span data-stu-id="89815-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="89815-113">Membros de struct não podem ser protegidos porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="89815-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="89815-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89815-114">Example</span></span>

<span data-ttu-id="89815-115">Nesse exemplo, a classe `DerivedPoint` é derivada de `Point`.</span><span class="sxs-lookup"><span data-stu-id="89815-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="89815-116">Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="89815-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="89815-117">Se você alterar os níveis de acesso de `x` e `y` para [private](private.md), o compilador emitirá as mensagens de erro:</span><span class="sxs-lookup"><span data-stu-id="89815-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="89815-118">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="89815-118">C# language specification</span></span>  

<span data-ttu-id="89815-119">Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="89815-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="89815-120">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="89815-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="89815-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="89815-121">See also</span></span>

- [<span data-ttu-id="89815-122">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="89815-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89815-123">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="89815-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="89815-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="89815-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="89815-125">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="89815-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="89815-126">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="89815-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="89815-127">Modificadores</span><span class="sxs-lookup"><span data-stu-id="89815-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="89815-128">public</span><span class="sxs-lookup"><span data-stu-id="89815-128">public</span></span>](public.md)
- [<span data-ttu-id="89815-129">particulares</span><span class="sxs-lookup"><span data-stu-id="89815-129">private</span></span>](private.md)
- [<span data-ttu-id="89815-130">interno</span><span class="sxs-lookup"><span data-stu-id="89815-130">internal</span></span>](internal.md)
- <span data-ttu-id="89815-131">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="89815-131">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
