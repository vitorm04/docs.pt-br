---
title: Palavra-chave public – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 15b86920736f1220553b462d103841ac98d88b7c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239297"
---
# <a name="public-c-reference"></a><span data-ttu-id="dcb42-102">public (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dcb42-102">public (C# Reference)</span></span>

<span data-ttu-id="dcb42-103">A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="dcb42-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="dcb42-104">Acesso público é o nível de acesso mais permissivo.</span><span class="sxs-lookup"><span data-stu-id="dcb42-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="dcb42-105">Não há nenhuma restrição quanto ao acesso a membros públicos, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="dcb42-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="dcb42-106">Consulte [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](accessibility-levels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="dcb42-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="dcb42-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb42-107">Example</span></span>

<span data-ttu-id="dcb42-108">No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="dcb42-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="dcb42-109">Os membros públicos `x` e `y` de `PointTest` são acessados diretamente de `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="dcb42-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="dcb42-110">Se alterar o nível de acesso de `public` para [particular](private.md) ou [protegido](protected.md), você receberá a mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="dcb42-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="dcb42-111">'PointTest.y' é inacessível devido ao seu nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="dcb42-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dcb42-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dcb42-112">C# language specification</span></span>  

<span data-ttu-id="dcb42-113">Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dcb42-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="dcb42-114">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="dcb42-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcb42-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb42-115">See also</span></span>

- [<span data-ttu-id="dcb42-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dcb42-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dcb42-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dcb42-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dcb42-118">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="dcb42-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="dcb42-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="dcb42-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dcb42-120">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="dcb42-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="dcb42-121">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="dcb42-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="dcb42-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="dcb42-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="dcb42-123">private</span><span class="sxs-lookup"><span data-stu-id="dcb42-123">private</span></span>](private.md)
- [<span data-ttu-id="dcb42-124">protected</span><span class="sxs-lookup"><span data-stu-id="dcb42-124">protected</span></span>](protected.md)
- [<span data-ttu-id="dcb42-125">internal</span><span class="sxs-lookup"><span data-stu-id="dcb42-125">internal</span></span>](internal.md)