---
title: "Modificadores de acesso (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a3ad46580561500d9f011da4997007023a3bc844
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="fccd6-102">Modificadores de acesso (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fccd6-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="fccd6-103">Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo.</span><span class="sxs-lookup"><span data-stu-id="fccd6-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="fccd6-104">Esta seção apresenta os quatro modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="fccd6-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="fccd6-105">public</span><span class="sxs-lookup"><span data-stu-id="fccd6-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="fccd6-106">protected</span><span class="sxs-lookup"><span data-stu-id="fccd6-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="fccd6-107">internal</span><span class="sxs-lookup"><span data-stu-id="fccd6-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="fccd6-108">private</span><span class="sxs-lookup"><span data-stu-id="fccd6-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="fccd6-109">Os cinco níveis de acessibilidade a seguir podem ser especificados usando os modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="fccd6-109">The following five accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="fccd6-110">`public`: o acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="fccd6-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="fccd6-111">`protected`: o acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="fccd6-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="fccd6-112">`Internal`: o acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="fccd6-112">`Internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="fccd6-113">[protegido interno](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md): o acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="fccd6-113">[protected internal](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="fccd6-114">`private`: o acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="fccd6-114">`private`: Access is limited to the containing type.</span></span>  
  
 <span data-ttu-id="fccd6-115">Esta seção também apresenta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fccd6-115">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="fccd6-116">[Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md): utilização dos quatro modificadores de acesso para declarar cinco níveis de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="fccd6-116">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare five levels of accessibility.</span></span>  
  
-   <span data-ttu-id="fccd6-117">[Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md): especifica em que lugar, nas seções do programa, um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="fccd6-117">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="fccd6-118">[Restrições no uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): um resumo das restrições sobre o uso de níveis de acessibilidade declarados.</span><span class="sxs-lookup"><span data-stu-id="fccd6-118">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccd6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fccd6-119">See Also</span></span>  
 <span data-ttu-id="fccd6-120">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fccd6-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fccd6-121">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fccd6-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fccd6-122">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="fccd6-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="fccd6-123">[Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="fccd6-123">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="fccd6-124">[Palavras-chave de acesso](../../../csharp/language-reference/keywords/access-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="fccd6-124">[Access Keywords](../../../csharp/language-reference/keywords/access-keywords.md) </span></span>  
 [<span data-ttu-id="fccd6-125">Modificadores</span><span class="sxs-lookup"><span data-stu-id="fccd6-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

