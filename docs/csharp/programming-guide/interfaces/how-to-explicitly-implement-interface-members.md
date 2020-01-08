---
title: Como implementar explicitamente membros de interface – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 4efc325b3587ee790cce739727506a28c3a1f524
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635399"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="695e2-102">Como implementar explicitamente membros de interface (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="695e2-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="695e2-103">Este exemplo declara uma [interface](../../language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box`, que implementa explicitamente os membros de interface `getLength` e `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="695e2-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="695e2-104">Os membros são acessados por meio da instância `dimensions` da interface.</span><span class="sxs-lookup"><span data-stu-id="695e2-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="695e2-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="695e2-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="695e2-106">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="695e2-106">Robust Programming</span></span>  
  
- <span data-ttu-id="695e2-107">Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="695e2-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="695e2-108">Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../language-reference/keywords/class.md):</span><span class="sxs-lookup"><span data-stu-id="695e2-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="695e2-109">Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:</span><span class="sxs-lookup"><span data-stu-id="695e2-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="695e2-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="695e2-110">See also</span></span>

- [<span data-ttu-id="695e2-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="695e2-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="695e2-112">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="695e2-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="695e2-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="695e2-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="695e2-114">Como implementar explicitamente membros de duas interfaces</span><span class="sxs-lookup"><span data-stu-id="695e2-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
