---
title: 'Como: implementar membros de duas interfaces explicitamente – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 3e03e80279db8c36cb975715f390ff6899d593cb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238319"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="dc332-102">Como: implementar membros de duas interfaces explicitamente (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="dc332-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="dc332-103">A implementação explícita da [interface](../../../csharp/language-reference/keywords/interface.md) também permite ao programador implementar duas interfaces que têm os mesmos nomes de membro e implementar separadamente cada membro de interface.</span><span class="sxs-lookup"><span data-stu-id="dc332-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="dc332-104">Este exemplo exibe as dimensões de uma caixa em unidades inglesas e no sistema métrico.</span><span class="sxs-lookup"><span data-stu-id="dc332-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="dc332-105">A Caixa [classe](../../../csharp/language-reference/keywords/class.md) implementa duas interfaces, IEnglishDimensions e IMetricDimensions, que representam os diferentes sistemas de medida.</span><span class="sxs-lookup"><span data-stu-id="dc332-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="dc332-106">As duas interfaces têm nomes de membro idênticos, Comprimento e Largura.</span><span class="sxs-lookup"><span data-stu-id="dc332-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc332-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc332-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dc332-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="dc332-108">Robust Programming</span></span>  
 <span data-ttu-id="dc332-109">Caso deseje que as medidas padrão estejam unidades inglesas, implemente os métodos Comprimento e Largura normalmente e implemente explicitamente os métodos Comprimento e Largura da interface IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="dc332-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="dc332-110">Nesse caso, é possível acessar as unidades inglesas da instância de classe e acessar as unidades métricas da instância da interface:</span><span class="sxs-lookup"><span data-stu-id="dc332-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="dc332-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc332-111">See Also</span></span>

- [<span data-ttu-id="dc332-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dc332-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dc332-113">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="dc332-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="dc332-114">Interfaces</span><span class="sxs-lookup"><span data-stu-id="dc332-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="dc332-115">Como: implementar membros de interface de forma explícita</span><span class="sxs-lookup"><span data-stu-id="dc332-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
