---
title: Como implementar explicitamente membros de duas interfaces – guia de programação C#
description: Saiba como implementar explicitamente duas interfaces que têm os mesmos nomes de membro e dar a cada membro da interface uma implementação separada neste exemplo de C#.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: d60ec43f734d5e8bfa7f467874440bd3514877fe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303056"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="c238b-103">Como implementar explicitamente membros de duas interfaces (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c238b-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="c238b-104">A implementação explícita da [interface](../../language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface.</span><span class="sxs-lookup"><span data-stu-id="c238b-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="c238b-105">Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico.</span><span class="sxs-lookup"><span data-stu-id="c238b-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="c238b-106">A Caixa [classe](../../language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida.</span><span class="sxs-lookup"><span data-stu-id="c238b-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="c238b-107">As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.</span><span class="sxs-lookup"><span data-stu-id="c238b-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c238b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c238b-108">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c238b-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c238b-109">Robust Programming</span></span>  
 <span data-ttu-id="c238b-110">Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="c238b-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="c238b-111">Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:</span><span class="sxs-lookup"><span data-stu-id="c238b-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c238b-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="c238b-112">See also</span></span>

- [<span data-ttu-id="c238b-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c238b-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c238b-114">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="c238b-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="c238b-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c238b-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="c238b-116">Como implementar membros de interface explicitamente</span><span class="sxs-lookup"><span data-stu-id="c238b-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
