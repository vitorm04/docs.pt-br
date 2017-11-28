---
title: "Domínio de acessibilidade (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="1a8df-102">Domínio de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1a8df-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="1a8df-103">O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="1a8df-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="1a8df-104">Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="1a8df-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="1a8df-105">O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="1a8df-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="1a8df-106">Isto é, o domínio inclui todos os arquivos de origem deste projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8df-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="1a8df-107">O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="1a8df-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="1a8df-108">Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="1a8df-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="1a8df-109">O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="1a8df-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="1a8df-110">Esses conceitos são demonstrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a8df-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a8df-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a8df-111">Example</span></span>  
 <span data-ttu-id="1a8df-112">Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`.</span><span class="sxs-lookup"><span data-stu-id="1a8df-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="1a8df-113">As classes contêm campos que têm diferentes acessibilidades declaradas.</span><span class="sxs-lookup"><span data-stu-id="1a8df-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="1a8df-114">No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro.</span><span class="sxs-lookup"><span data-stu-id="1a8df-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="1a8df-115">Observe que as instruções que tentam fazer referência aos membros inacessíveis são tornadas inertes ao serem transformadas em comentários. Se você quiser ver os erros de compilador causados ao referenciar um membro inacessível, remova os comentários um por vez.</span><span class="sxs-lookup"><span data-stu-id="1a8df-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a8df-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1a8df-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a8df-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a8df-117">See Also</span></span>  
 [<span data-ttu-id="1a8df-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1a8df-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1a8df-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1a8df-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1a8df-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1a8df-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1a8df-121">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="1a8df-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="1a8df-122">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1a8df-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="1a8df-123">Restrições ao uso de níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1a8df-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="1a8df-124">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="1a8df-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="1a8df-125">public</span><span class="sxs-lookup"><span data-stu-id="1a8df-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="1a8df-126">private</span><span class="sxs-lookup"><span data-stu-id="1a8df-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="1a8df-127">protected</span><span class="sxs-lookup"><span data-stu-id="1a8df-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="1a8df-128">internal</span><span class="sxs-lookup"><span data-stu-id="1a8df-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
