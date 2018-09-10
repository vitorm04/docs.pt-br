---
title: Palavra-chave public (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518180"
---
# <a name="public-c-reference"></a><span data-ttu-id="7f862-102">public (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7f862-102">public (C# Reference)</span></span>

<span data-ttu-id="7f862-103">A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="7f862-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="7f862-104">Acesso público é o nível de acesso mais permissivo.</span><span class="sxs-lookup"><span data-stu-id="7f862-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="7f862-105">Não há nenhuma restrição quanto ao acesso a membros públicos, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="7f862-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="7f862-106">Consulte [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](accessibility-levels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7f862-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="7f862-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f862-107">Example</span></span>

<span data-ttu-id="7f862-108">No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7f862-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="7f862-109">Os membros públicos `x` e `y` de `PointTest` são acessados diretamente de `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7f862-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="7f862-110">Se alterar o nível de acesso de `public` para [particular](private.md) ou [protegido](protected.md), você receberá a mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="7f862-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="7f862-111">'PointTest.y' é inacessível devido ao seu nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="7f862-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f862-112">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7f862-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7f862-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f862-113">See also</span></span>

- [<span data-ttu-id="7f862-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7f862-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f862-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7f862-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f862-116">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="7f862-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="7f862-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7f862-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7f862-118">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="7f862-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="7f862-119">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="7f862-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="7f862-120">Modificadores</span><span class="sxs-lookup"><span data-stu-id="7f862-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="7f862-121">private</span><span class="sxs-lookup"><span data-stu-id="7f862-121">private</span></span>](private.md)
- [<span data-ttu-id="7f862-122">protected</span><span class="sxs-lookup"><span data-stu-id="7f862-122">protected</span></span>](protected.md)
- [<span data-ttu-id="7f862-123">internal</span><span class="sxs-lookup"><span data-stu-id="7f862-123">internal</span></span>](internal.md)