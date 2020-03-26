---
title: Como fazer teste de clique em um Viewport3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D visuals [WPF], hit-testing for
- hit tests [WPF], for 3D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 34bc86349332293e40aca5743cbabb2a48634da6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112083"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="a45b6-102">Como fazer teste de clique em um Viewport3D</span><span class="sxs-lookup"><span data-stu-id="a45b6-102">How to: Hit Test in a Viewport3D</span></span>

<span data-ttu-id="a45b6-103">Este exemplo mostra como acertar o teste <xref:System.Windows.Controls.Viewport3D>para visuais 3D em um .</span><span class="sxs-lookup"><span data-stu-id="a45b6-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>

<span data-ttu-id="a45b6-104">Como <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retorna informações 2D e 3D, é possível iterar através dos resultados do teste para ler apenas os resultados 3D.</span><span class="sxs-lookup"><span data-stu-id="a45b6-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

<span data-ttu-id="a45b6-105">O <xref:System.Windows.Media.HitTestResultBehavior> código a seguir determina como os resultados do teste de acerto são processados.</span><span class="sxs-lookup"><span data-stu-id="a45b6-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span> <span data-ttu-id="a45b6-106">`UpdateResultInfo`e `UpdateMaterial` são métodos definidos localmente.</span><span class="sxs-lookup"><span data-stu-id="a45b6-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
