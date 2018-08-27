---
title: public (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 853f9c9ebe36345a897337d4e793d3c88059e068
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998721"
---
# <a name="public-c-reference"></a><span data-ttu-id="2724b-102">public (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2724b-102">public (C# Reference)</span></span>
<span data-ttu-id="2724b-103">A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="2724b-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="2724b-104">Acesso público é o nível de acesso mais permissivo.</span><span class="sxs-lookup"><span data-stu-id="2724b-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="2724b-105">Não há nenhuma restrição quanto ao acesso a membros públicos, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="2724b-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="2724b-106">Consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2724b-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2724b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2724b-107">Example</span></span>  
 <span data-ttu-id="2724b-108">No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="2724b-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="2724b-109">Os membros públicos `x` e `y` de `PointTest` são acessados diretamente de `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="2724b-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="2724b-110">Se alterar o nível de acesso de `public` para [particular](../../../csharp/language-reference/keywords/private.md) ou [protegido](../../../csharp/language-reference/keywords/protected.md), você receberá a mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="2724b-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="2724b-111">'PointTest.y' é inacessível devido ao seu nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="2724b-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2724b-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2724b-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2724b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2724b-113">See Also</span></span>

- [<span data-ttu-id="2724b-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2724b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2724b-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2724b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2724b-116">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="2724b-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="2724b-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2724b-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2724b-118">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="2724b-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="2724b-119">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="2724b-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="2724b-120">Modificadores</span><span class="sxs-lookup"><span data-stu-id="2724b-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="2724b-121">private</span><span class="sxs-lookup"><span data-stu-id="2724b-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="2724b-122">protected</span><span class="sxs-lookup"><span data-stu-id="2724b-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
- [<span data-ttu-id="2724b-123">internal</span><span class="sxs-lookup"><span data-stu-id="2724b-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
