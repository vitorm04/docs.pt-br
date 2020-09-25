---
title: Como implementar explicitamente membros de duas interfaces – guia de programação C#
description: Saiba como implementar explicitamente duas interfaces que têm os mesmos nomes de membro e dar a cada membro da interface uma implementação separada neste exemplo de C#.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 18b1f9cfb1690d35c0bca0a3c79c1b80ae5dd44d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205081"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="1e7b2-103">Como implementar explicitamente membros de duas interfaces (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1e7b2-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="1e7b2-104">A implementação explícita da [interface](../../language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface.</span><span class="sxs-lookup"><span data-stu-id="1e7b2-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="1e7b2-105">Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico.</span><span class="sxs-lookup"><span data-stu-id="1e7b2-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="1e7b2-106">A Caixa [classe](../../language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida.</span><span class="sxs-lookup"><span data-stu-id="1e7b2-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="1e7b2-107">As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.</span><span class="sxs-lookup"><span data-stu-id="1e7b2-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e7b2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e7b2-108">Example</span></span>  

 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1e7b2-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1e7b2-109">Robust Programming</span></span>  

 <span data-ttu-id="1e7b2-110">Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="1e7b2-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="1e7b2-111">Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:</span><span class="sxs-lookup"><span data-stu-id="1e7b2-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1e7b2-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="1e7b2-112">See also</span></span>

- [<span data-ttu-id="1e7b2-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1e7b2-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1e7b2-114">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="1e7b2-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1e7b2-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="1e7b2-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1e7b2-116">Como implementar membros de interface explicitamente</span><span class="sxs-lookup"><span data-stu-id="1e7b2-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
