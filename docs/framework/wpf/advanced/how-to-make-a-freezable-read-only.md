---
title: Como tornar um congelável somente leitura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460077"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="5a565-102">Como tornar um congelável somente leitura</span><span class="sxs-lookup"><span data-stu-id="5a565-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="5a565-103">Este exemplo mostra como tornar um <xref:System.Windows.Freezable> somente leitura chamando seu método <xref:System.Windows.Freezable.Freeze%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a565-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="5a565-104">Você não poderá congelar um objeto <xref:System.Windows.Freezable> se qualquer uma das condições a seguir for `true` sobre o objeto:</span><span class="sxs-lookup"><span data-stu-id="5a565-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="5a565-105">Ele tem propriedades animadas ou associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="5a565-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="5a565-106">Ele tem propriedades que são definidas por um recurso dinâmico.</span><span class="sxs-lookup"><span data-stu-id="5a565-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="5a565-107">Para obter mais informações sobre recursos dinâmicos, consulte os [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="5a565-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="5a565-108">Ele contém <xref:System.Windows.Freezable> subobjetos que não podem ser congelados.</span><span class="sxs-lookup"><span data-stu-id="5a565-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="5a565-109">Se essas condições forem `false`das para o objeto <xref:System.Windows.Freezable> e você não pretender modificá-lo, considere a possibilidade de congelá-lo para obter benefícios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="5a565-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a565-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a565-110">Example</span></span>  
 <span data-ttu-id="5a565-111">O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush>, que é um tipo de objeto <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="5a565-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="5a565-112">Para obter mais informações sobre objetos <xref:System.Windows.Freezable>, consulte a [visão geral dos objetos Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a565-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a565-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a565-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="5a565-114">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="5a565-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="5a565-115">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="5a565-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
