---
title: 'Como: implementar membros de interface explicitamente – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 064061b44cca3adb5dde89ecc71fb1f8ea3abf8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562891"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="76c48-102">Como: implementar membros de interface explicitamente (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="76c48-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="76c48-103">Este exemplo declara uma [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box`, que implementa explicitamente os membros de interface `getLength` e `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="76c48-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="76c48-104">Os membros são acessados por meio da instância `dimensions` da interface.</span><span class="sxs-lookup"><span data-stu-id="76c48-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c48-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76c48-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="76c48-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="76c48-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="76c48-107">Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="76c48-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="76c48-108">Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../../csharp/language-reference/keywords/class.md):</span><span class="sxs-lookup"><span data-stu-id="76c48-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="76c48-109">Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:</span><span class="sxs-lookup"><span data-stu-id="76c48-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="76c48-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76c48-110">See also</span></span>

- [<span data-ttu-id="76c48-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="76c48-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="76c48-112">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="76c48-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="76c48-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="76c48-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="76c48-114">Como: implementar membros de duas interfaces de forma explícita</span><span class="sxs-lookup"><span data-stu-id="76c48-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
