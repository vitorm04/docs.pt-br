---
title: Como fazer teste de clique em um Viewport3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733375"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="388b1-102">Como fazer teste de clique em um Viewport3D</span><span class="sxs-lookup"><span data-stu-id="388b1-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="388b1-103">Este exemplo mostra como testar ocorrências de elementos visuais 3D em um <xref:System.Windows.Controls.Viewport3D>.</span><span class="sxs-lookup"><span data-stu-id="388b1-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="388b1-104">Porque <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retorna informações 2D e 3D, é possível iterar os resultados do teste para ler somente os resultados 3D.</span><span class="sxs-lookup"><span data-stu-id="388b1-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="388b1-105">O <xref:System.Windows.Media.HitTestResultBehavior> no código a seguir determina como os resultados de teste de clique são processados.</span><span class="sxs-lookup"><span data-stu-id="388b1-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="388b1-106">`UpdateResultInfo` e `UpdateMaterial` são métodos definidos localmente.</span><span class="sxs-lookup"><span data-stu-id="388b1-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="388b1-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="388b1-107">See Also</span></span>  
 [<span data-ttu-id="388b1-108">Exemplo de teste de ocorrências de 3D</span><span class="sxs-lookup"><span data-stu-id="388b1-108">3-D Hit Testing Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159959)
