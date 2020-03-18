---
title: Domínio de acessibilidade – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713831"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="82e03-102">Domínio de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="82e03-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="82e03-103">O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="82e03-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="82e03-104">Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](./accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="82e03-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="82e03-105">O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="82e03-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="82e03-106">Isto é, o domínio inclui todos os arquivos de origem deste projeto.</span><span class="sxs-lookup"><span data-stu-id="82e03-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="82e03-107">O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="82e03-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="82e03-108">Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="82e03-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="82e03-109">O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="82e03-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="82e03-110">Esses conceitos são demonstrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="82e03-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e03-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82e03-111">Example</span></span>  
 <span data-ttu-id="82e03-112">Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`.</span><span class="sxs-lookup"><span data-stu-id="82e03-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="82e03-113">As classes contêm campos que têm diferentes acessibilidades declaradas.</span><span class="sxs-lookup"><span data-stu-id="82e03-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="82e03-114">No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro.</span><span class="sxs-lookup"><span data-stu-id="82e03-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="82e03-115">Observe que as declarações que tentam referenciar os membros inacessíveis são comentadas. Se você quiser ver os erros de compilação causados pela referência a um membro inacessível, remova os comentários um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="82e03-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="82e03-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="82e03-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82e03-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="82e03-117">See also</span></span>

- [<span data-ttu-id="82e03-118">C# Referência</span><span class="sxs-lookup"><span data-stu-id="82e03-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="82e03-119">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="82e03-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82e03-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="82e03-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="82e03-121">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="82e03-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="82e03-122">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="82e03-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="82e03-123">Restrições ao uso de níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="82e03-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="82e03-124">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="82e03-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="82e03-125">público</span><span class="sxs-lookup"><span data-stu-id="82e03-125">public</span></span>](./public.md)
- [<span data-ttu-id="82e03-126">Privada</span><span class="sxs-lookup"><span data-stu-id="82e03-126">private</span></span>](./private.md)
- [<span data-ttu-id="82e03-127">Protegido</span><span class="sxs-lookup"><span data-stu-id="82e03-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="82e03-128">Interno</span><span class="sxs-lookup"><span data-stu-id="82e03-128">internal</span></span>](./internal.md)
