---
title: Palavra-chave protected (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 6e3f72226d10910152f7a2139a5a1be35e681ec7
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50183172"
---
# <a name="protected-c-reference"></a><span data-ttu-id="d2aa4-102">protected (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d2aa4-102">protected (C# Reference)</span></span>

<span data-ttu-id="d2aa4-103">A palavra-chave `protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="d2aa4-104">Esta página aborda o acesso `protected`.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-104">This page covers `protected` access.</span></span> <span data-ttu-id="d2aa4-105">A palavra-chave `protected` também faz parte dos modificadores de acesso [`protected internal`](protected-internal.md) e [`private protected`](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="d2aa4-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="d2aa4-106">Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="d2aa4-107">Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d2aa4-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2aa4-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2aa4-108">Example</span></span>

<span data-ttu-id="d2aa4-109">Um membro protegido de uma classe base será acessível em uma classe derivada somente se o acesso ocorrer por meio do tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="d2aa4-110">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="d2aa4-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="d2aa4-111">A instrução `a.x = 10` gera um erro porque ela é feita dentro do método estático Main e não em uma instância da classe B.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="d2aa4-112">Membros de struct não podem ser protegidos porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="d2aa4-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2aa4-113">Example</span></span>

<span data-ttu-id="d2aa4-114">Nesse exemplo, a classe `DerivedPoint` é derivada de `Point`.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="d2aa4-115">Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="d2aa4-116">Se você alterar os níveis de acesso de `x` e `y` para [private](private.md), o compilador emitirá as mensagens de erro:</span><span class="sxs-lookup"><span data-stu-id="d2aa4-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="d2aa4-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d2aa4-117">C# language specification</span></span>  

<span data-ttu-id="d2aa4-118">Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2aa4-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="d2aa4-119">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="d2aa4-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2aa4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2aa4-120">See also</span></span>

- [<span data-ttu-id="d2aa4-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d2aa4-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d2aa4-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d2aa4-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d2aa4-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d2aa4-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d2aa4-124">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="d2aa4-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="d2aa4-125">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="d2aa4-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="d2aa4-126">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d2aa4-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="d2aa4-127">public</span><span class="sxs-lookup"><span data-stu-id="d2aa4-127">public</span></span>](public.md)
- [<span data-ttu-id="d2aa4-128">private</span><span class="sxs-lookup"><span data-stu-id="d2aa4-128">private</span></span>](private.md)
- [<span data-ttu-id="d2aa4-129">internal</span><span class="sxs-lookup"><span data-stu-id="d2aa4-129">internal</span></span>](internal.md)
- <span data-ttu-id="d2aa4-130">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2aa4-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>