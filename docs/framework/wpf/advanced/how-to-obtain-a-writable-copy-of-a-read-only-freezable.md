---
title: "Como obter uma cópia gravável de um congelável somente leitura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe22e49ee28de60bc76d7a4f543462bbcfac48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="42a91-102">Como obter uma cópia gravável de um congelável somente leitura</span><span class="sxs-lookup"><span data-stu-id="42a91-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="42a91-103">Este exemplo mostra como usar o <xref:System.Windows.Freezable.Clone%2A> método para criar uma cópia gravável somente leitura <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="42a91-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="42a91-104">Após um <xref:System.Windows.Freezable> objeto está marcado como somente leitura ("congelado"), você não pode modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="42a91-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="42a91-105">No entanto, você pode usar o <xref:System.Windows.Freezable.Clone%2A> método para criar um clone modificável do objeto congelado.</span><span class="sxs-lookup"><span data-stu-id="42a91-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42a91-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42a91-106">Example</span></span>  
 <span data-ttu-id="42a91-107">O exemplo a seguir cria um clone modificável de um congelada <xref:System.Windows.Media.SolidColorBrush> objeto.</span><span class="sxs-lookup"><span data-stu-id="42a91-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="42a91-108">Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="42a91-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a91-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42a91-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [<span data-ttu-id="42a91-110">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="42a91-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="42a91-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="42a91-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
