---
title: Palavra-chave protected (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: cc3c8f81edb68fb26be560c8635e30dfd6e7b372
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50183172"
---
# <a name="protected-c-reference"></a><span data-ttu-id="3e479-102">protected (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3e479-102">protected (C# Reference)</span></span>

<span data-ttu-id="3e479-103">A palavra-chave `protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="3e479-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="3e479-104">Esta página aborda o acesso `protected`.</span><span class="sxs-lookup"><span data-stu-id="3e479-104">This page covers `protected` access.</span></span> <span data-ttu-id="3e479-105">A palavra-chave `protected` também faz parte dos modificadores de acesso [`protected internal`](protected-internal.md) e [`private protected`](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="3e479-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="3e479-106">Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3e479-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="3e479-107">Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3e479-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="3e479-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e479-108">Example</span></span>

<span data-ttu-id="3e479-109">Um membro protegido de uma classe base será acessível em uma classe derivada somente se o acesso ocorrer por meio do tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3e479-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="3e479-110">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="3e479-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="3e479-111">A instrução `a.x = 10` gera um erro porque ela é feita dentro do método estático Main e não em uma instância da classe B.</span><span class="sxs-lookup"><span data-stu-id="3e479-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="3e479-112">Membros de struct não podem ser protegidos porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="3e479-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="3e479-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e479-113">Example</span></span>

<span data-ttu-id="3e479-114">Nesse exemplo, a classe `DerivedPoint` é derivada de `Point`.</span><span class="sxs-lookup"><span data-stu-id="3e479-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="3e479-115">Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3e479-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="3e479-116">Se você alterar os níveis de acesso de `x` e `y` para [private](private.md), o compilador emitirá as mensagens de erro:</span><span class="sxs-lookup"><span data-stu-id="3e479-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="3e479-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3e479-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3e479-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e479-118">See also</span></span>

- [<span data-ttu-id="3e479-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3e479-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3e479-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3e479-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3e479-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3e479-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3e479-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="3e479-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3e479-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="3e479-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3e479-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="3e479-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="3e479-125">public</span><span class="sxs-lookup"><span data-stu-id="3e479-125">public</span></span>](public.md)
- [<span data-ttu-id="3e479-126">private</span><span class="sxs-lookup"><span data-stu-id="3e479-126">private</span></span>](private.md)
- [<span data-ttu-id="3e479-127">internal</span><span class="sxs-lookup"><span data-stu-id="3e479-127">internal</span></span>](internal.md)
- <span data-ttu-id="3e479-128">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e479-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>