---
title: Como implementar explicitamente membros da interface - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627779"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="0ba1a-102">Como implementar explicitamente membros de interface (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0ba1a-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="0ba1a-103">Este exemplo declara [interface](../../language-reference/keywords/interface.md)uma `IDimensions`interface , `Box`e uma classe, que `GetLength` implementa explicitamente os membros da interface e `GetWidth`.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="0ba1a-104">Os membros são acessados por meio da instância `dimensions` da interface.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ba1a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ba1a-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0ba1a-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0ba1a-106">Robust Programming</span></span>  
  
- <span data-ttu-id="0ba1a-107">Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="0ba1a-108">Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../language-reference/keywords/class.md):</span><span class="sxs-lookup"><span data-stu-id="0ba1a-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="0ba1a-109">Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:</span><span class="sxs-lookup"><span data-stu-id="0ba1a-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="0ba1a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ba1a-110">See also</span></span>

- [<span data-ttu-id="0ba1a-111">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="0ba1a-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0ba1a-112">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="0ba1a-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="0ba1a-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="0ba1a-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="0ba1a-114">Como implementar membros de duas interfaces explicitamente</span><span class="sxs-lookup"><span data-stu-id="0ba1a-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
