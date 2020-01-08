---
title: Como implementar explicitamente membros de duas interfaces – guia C# de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 720e265cedcf9ad8be00f5e013365129f38749af
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635243"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="86418-102">Como implementar explicitamente membros de duas interfaces (guiaC# de programação)</span><span class="sxs-lookup"><span data-stu-id="86418-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="86418-103">A implementação explícita da [interface](../../language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface.</span><span class="sxs-lookup"><span data-stu-id="86418-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="86418-104">Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico.</span><span class="sxs-lookup"><span data-stu-id="86418-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="86418-105">A Caixa [classe](../../language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida.</span><span class="sxs-lookup"><span data-stu-id="86418-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="86418-106">As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.</span><span class="sxs-lookup"><span data-stu-id="86418-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86418-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86418-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="86418-108">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="86418-108">Robust Programming</span></span>  
 <span data-ttu-id="86418-109">Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="86418-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="86418-110">Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:</span><span class="sxs-lookup"><span data-stu-id="86418-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="86418-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="86418-111">See also</span></span>

- [<span data-ttu-id="86418-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="86418-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86418-113">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="86418-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="86418-114">Interfaces</span><span class="sxs-lookup"><span data-stu-id="86418-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="86418-115">Como implementar explicitamente membros de interface</span><span class="sxs-lookup"><span data-stu-id="86418-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
