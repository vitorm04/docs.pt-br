---
description: Domínio de acessibilidade – Referência de C#
title: Domínio de acessibilidade – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127055"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="1f3e2-103">Domínio de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1f3e2-103">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="1f3e2-104">O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-104">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="1f3e2-105">Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](./accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-105">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="1f3e2-106">O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-106">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="1f3e2-107">Isto é, o domínio inclui todos os arquivos de origem deste projeto.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-107">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="1f3e2-108">O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-108">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="1f3e2-109">Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-109">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="1f3e2-110">O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-110">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="1f3e2-111">Esses conceitos são demonstrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-111">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3e2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1f3e2-112">Example</span></span>  
 <span data-ttu-id="1f3e2-113">Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-113">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="1f3e2-114">As classes contêm campos que têm diferentes acessibilidades declaradas.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-114">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="1f3e2-115">No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-115">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="1f3e2-116">Observe que as instruções que tentam referenciar os membros inacessíveis são comentadas. Se você quiser ver os erros do compilador causados pela referência a um membro inacessível, remova os comentários um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="1f3e2-116">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="1f3e2-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1f3e2-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f3e2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f3e2-118">See also</span></span>

- [<span data-ttu-id="1f3e2-119">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="1f3e2-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f3e2-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1f3e2-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f3e2-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1f3e2-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1f3e2-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="1f3e2-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="1f3e2-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1f3e2-123">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="1f3e2-124">Restrições ao uso de níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1f3e2-124">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="1f3e2-125">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="1f3e2-125">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="1f3e2-126">public</span><span class="sxs-lookup"><span data-stu-id="1f3e2-126">public</span></span>](./public.md)
- [<span data-ttu-id="1f3e2-127">particulares</span><span class="sxs-lookup"><span data-stu-id="1f3e2-127">private</span></span>](./private.md)
- [<span data-ttu-id="1f3e2-128">protegidos</span><span class="sxs-lookup"><span data-stu-id="1f3e2-128">protected</span></span>](./protected.md)
- [<span data-ttu-id="1f3e2-129">interno</span><span class="sxs-lookup"><span data-stu-id="1f3e2-129">internal</span></span>](./internal.md)
