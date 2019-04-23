---
title: 'Como: Determinar se um congelável está congelado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 6a63862d35f2c40289ea6445eb3dab8a2abe4a61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197055"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="97630-102">Como: Determinar se um congelável está congelado</span><span class="sxs-lookup"><span data-stu-id="97630-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="97630-103">Este exemplo mostra como determinar se um <xref:System.Windows.Freezable> objeto é congelado.</span><span class="sxs-lookup"><span data-stu-id="97630-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="97630-104">Se você tentar modificar um congelado <xref:System.Windows.Freezable> do objeto, ele gerará um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="97630-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="97630-105">Para evitar gerar essa exceção, use o <xref:System.Windows.Freezable.IsFrozen%2A> propriedade do <xref:System.Windows.Freezable> objeto para determinar se ele está congelado.</span><span class="sxs-lookup"><span data-stu-id="97630-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97630-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97630-106">Example</span></span>  
 <span data-ttu-id="97630-107">O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush> e, em seguida, testa-o usando o <xref:System.Windows.Freezable.IsFrozen%2A> propriedade para determinar se ele está congelado.</span><span class="sxs-lookup"><span data-stu-id="97630-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="97630-108">Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte a [visão geral de objetos congeláveis](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="97630-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97630-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97630-109">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="97630-110">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="97630-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="97630-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="97630-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
