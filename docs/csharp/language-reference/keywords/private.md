---
description: Palavra-chave private – Referência de C#
title: Palavra-chave private – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139392"
---
# <a name="private-c-reference"></a><span data-ttu-id="ea391-103">private (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ea391-103">private (C# Reference)</span></span>

<span data-ttu-id="ea391-104">A palavra-chave `private` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="ea391-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="ea391-105">Esta página aborda o acesso `private`.</span><span class="sxs-lookup"><span data-stu-id="ea391-105">This page covers `private` access.</span></span> <span data-ttu-id="ea391-106">A `private` palavra-chave também faz parte do [`private protected`](./private-protected.md) modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="ea391-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="ea391-107">Acesso particular é o nível de acesso menos permissivo.</span><span class="sxs-lookup"><span data-stu-id="ea391-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="ea391-108">Membros particulares são acessíveis somente dentro do corpo da classe ou do struct em que são declarados, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea391-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="ea391-109">Tipos aninhados no mesmo corpo também podem acessar os membros particulares.</span><span class="sxs-lookup"><span data-stu-id="ea391-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="ea391-110">É um erro em tempo de compilação fazer referência a um membro particular fora da classe ou do struct em que ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="ea391-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="ea391-111">Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md) e [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ea391-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="ea391-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea391-112">Example</span></span>

<span data-ttu-id="ea391-113">Neste exemplo, a classe `Employee` contém dois membros de dados particulares, `name` e `salary`.</span><span class="sxs-lookup"><span data-stu-id="ea391-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="ea391-114">Como membros particulares, eles não podem ser acessados, exceto por métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="ea391-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="ea391-115">Métodos públicos chamados `GetName` e `Salary` foram adicionados para permitir acesso controlado aos membros particulares.</span><span class="sxs-lookup"><span data-stu-id="ea391-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="ea391-116">O membro `name` é acessado por meio de um método público e o membro `salary` é acessado por meio de uma propriedade somente leitura pública.</span><span class="sxs-lookup"><span data-stu-id="ea391-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="ea391-117">(Consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="ea391-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="ea391-118">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ea391-118">C# language specification</span></span>  

<span data-ttu-id="ea391-119">Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="ea391-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ea391-120">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="ea391-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea391-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ea391-121">See also</span></span>

- [<span data-ttu-id="ea391-122">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="ea391-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ea391-123">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="ea391-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ea391-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ea391-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ea391-125">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="ea391-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="ea391-126">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="ea391-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="ea391-127">Modificadores</span><span class="sxs-lookup"><span data-stu-id="ea391-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ea391-128">public</span><span class="sxs-lookup"><span data-stu-id="ea391-128">public</span></span>](public.md)
- [<span data-ttu-id="ea391-129">protegidos</span><span class="sxs-lookup"><span data-stu-id="ea391-129">protected</span></span>](protected.md)
- [<span data-ttu-id="ea391-130">interno</span><span class="sxs-lookup"><span data-stu-id="ea391-130">internal</span></span>](internal.md)
