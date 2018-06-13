---
title: Como implementar membros de interface explicitamente (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332180"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="76318-102">Como implementar membros de interface explicitamente (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="76318-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="76318-103">Este exemplo declara uma [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box`, que implementa explicitamente os membros de interface `getLength` e `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="76318-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="76318-104">Os membros são acessados por meio da instância `dimensions` da interface.</span><span class="sxs-lookup"><span data-stu-id="76318-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76318-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76318-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="76318-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="76318-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="76318-107">Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="76318-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="76318-108">Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../../csharp/language-reference/keywords/class.md):</span><span class="sxs-lookup"><span data-stu-id="76318-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="76318-109">Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:</span><span class="sxs-lookup"><span data-stu-id="76318-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="76318-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76318-110">See Also</span></span>  
 [<span data-ttu-id="76318-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="76318-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76318-112">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="76318-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="76318-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="76318-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="76318-114">Como implementar membros de duas interfaces explicitamente</span><span class="sxs-lookup"><span data-stu-id="76318-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
