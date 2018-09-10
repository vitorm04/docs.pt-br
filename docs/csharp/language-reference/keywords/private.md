---
title: Palavra-chave private (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 0c564f38940e993bdfb93af0ec995c684be0eeb7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43802710"
---
# <a name="private-c-reference"></a><span data-ttu-id="4d676-102">private (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4d676-102">private (C# Reference)</span></span>

<span data-ttu-id="4d676-103">A palavra-chave `private` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="4d676-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="4d676-104">Esta página aborda o acesso `private`.</span><span class="sxs-lookup"><span data-stu-id="4d676-104">This page covers `private` access.</span></span> <span data-ttu-id="4d676-105">A palavra-chave `private` também faz parte do modificador de acesso [`private protected`](./private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="4d676-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="4d676-106">Acesso particular é o nível de acesso menos permissivo.</span><span class="sxs-lookup"><span data-stu-id="4d676-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="4d676-107">Membros particulares são acessíveis somente dentro do corpo da classe ou do struct em que são declarados, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="4d676-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="4d676-108">Tipos aninhados no mesmo corpo também podem acessar os membros particulares.</span><span class="sxs-lookup"><span data-stu-id="4d676-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="4d676-109">É um erro em tempo de compilação fazer referência a um membro particular fora da classe ou do struct em que ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="4d676-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="4d676-110">Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md) e [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4d676-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d676-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d676-111">Example</span></span>

<span data-ttu-id="4d676-112">Neste exemplo, a classe `Employee` contém dois membros de dados particulares, `name` e `salary`.</span><span class="sxs-lookup"><span data-stu-id="4d676-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="4d676-113">Como membros particulares, eles não podem ser acessados, exceto por métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="4d676-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="4d676-114">Métodos públicos chamados `GetName` e `Salary` foram adicionados para permitir acesso controlado aos membros particulares.</span><span class="sxs-lookup"><span data-stu-id="4d676-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="4d676-115">O membro `name` é acessado por meio de um método público e o membro `salary` é acessado por meio de uma propriedade somente leitura pública.</span><span class="sxs-lookup"><span data-stu-id="4d676-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="4d676-116">(Consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="4d676-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="4d676-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4d676-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4d676-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d676-118">See also</span></span>

- [<span data-ttu-id="4d676-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4d676-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4d676-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4d676-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4d676-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4d676-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4d676-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="4d676-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="4d676-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="4d676-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="4d676-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="4d676-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="4d676-125">public</span><span class="sxs-lookup"><span data-stu-id="4d676-125">public</span></span>](public.md)
- [<span data-ttu-id="4d676-126">protected</span><span class="sxs-lookup"><span data-stu-id="4d676-126">protected</span></span>](protected.md)
- [<span data-ttu-id="4d676-127">internal</span><span class="sxs-lookup"><span data-stu-id="4d676-127">internal</span></span>](internal.md)