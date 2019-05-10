---
title: 'Como: Tornar um congelável somente leitura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 5748b7929db18578bbe00e3217b1578ac5fbc0f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614597"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="d71bc-102">Como: Tornar um congelável somente leitura</span><span class="sxs-lookup"><span data-stu-id="d71bc-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="d71bc-103">Este exemplo mostra como fazer uma <xref:System.Windows.Freezable> somente leitura, chamando seu <xref:System.Windows.Freezable.Freeze%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d71bc-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="d71bc-104">Você não é possível congelar um <xref:System.Windows.Freezable> do objeto se qualquer uma das seguintes condições for `true` sobre o objeto:</span><span class="sxs-lookup"><span data-stu-id="d71bc-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="d71bc-105">Ele tem propriedades animadas ou associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="d71bc-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="d71bc-106">Ela tem propriedades que são definidas por um recurso dinâmico.</span><span class="sxs-lookup"><span data-stu-id="d71bc-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="d71bc-107">Para obter mais informações sobre recursos dinâmicos, consulte o [recursos XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="d71bc-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
- <span data-ttu-id="d71bc-108">Ele contém <xref:System.Windows.Freezable> subobjetos não podem ser congelados.</span><span class="sxs-lookup"><span data-stu-id="d71bc-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="d71bc-109">Se essas condições forem `false` para seu <xref:System.Windows.Freezable> objeto e não pretende modificá-lo, considere congelá-lo para obter benefícios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d71bc-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71bc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d71bc-110">Example</span></span>  
 <span data-ttu-id="d71bc-111">O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush>, que é um tipo de <xref:System.Windows.Freezable> objeto.</span><span class="sxs-lookup"><span data-stu-id="d71bc-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="d71bc-112">Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte a [visão geral de objetos congeláveis](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d71bc-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71bc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d71bc-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="d71bc-114">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="d71bc-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="d71bc-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="d71bc-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
