---
title: Como implementar explicitamente membros de interface – guia de programação C#
description: Saiba como implementar explicitamente membros de interface neste exemplo de C#. Os membros são acessados por meio da instância de interface.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303069"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="1abf6-104">Como implementar explicitamente membros de interface (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1abf6-104">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="1abf6-105">Este exemplo declara uma [interface](../../language-reference/keywords/interface.md), `IDimensions` e uma classe, `Box` , que implementa explicitamente os membros da interface `GetLength` e `GetWidth` .</span><span class="sxs-lookup"><span data-stu-id="1abf6-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="1abf6-106">Os membros são acessados por meio da instância `dimensions` da interface.</span><span class="sxs-lookup"><span data-stu-id="1abf6-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1abf6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1abf6-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1abf6-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1abf6-108">Robust Programming</span></span>  
  
- <span data-ttu-id="1abf6-109">Observe que as seguintes linhas, no método `Main`, foram comentadas, pois produziriam erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="1abf6-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="1abf6-110">Um membro de interface implementado explicitamente não pode ser acessado de uma instância de [classe](../../language-reference/keywords/class.md):</span><span class="sxs-lookup"><span data-stu-id="1abf6-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="1abf6-111">Observe também que as linhas a seguir, no método `Main`, imprimem com êxito as dimensões da caixa, pois os métodos estão sendo chamados de uma instância da interface:</span><span class="sxs-lookup"><span data-stu-id="1abf6-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="1abf6-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="1abf6-112">See also</span></span>

- [<span data-ttu-id="1abf6-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1abf6-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1abf6-114">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="1abf6-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1abf6-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="1abf6-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1abf6-116">Como implementar membros de duas interfaces explicitamente</span><span class="sxs-lookup"><span data-stu-id="1abf6-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
