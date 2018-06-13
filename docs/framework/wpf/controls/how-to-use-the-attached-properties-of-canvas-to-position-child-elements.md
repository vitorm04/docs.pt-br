---
title: Como usar as propriedades anexas de tela para posicionar elementos filho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 886440304dc1bebdcfae66676254bef7ac35457d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552368"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="6f901-102">Como usar as propriedades anexas de tela para posicionar elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f901-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="6f901-103">Este exemplo mostra como usar as propriedades anexas de <xref:System.Windows.Controls.Canvas> para posicionar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="6f901-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f901-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f901-104">Example</span></span>  
 <span data-ttu-id="6f901-105">O exemplo a seguir adiciona quatro <xref:System.Windows.Controls.Button> elementos como elementos filho de um pai <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="6f901-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="6f901-106">Cada elemento filho representa uma propriedade anexa distinta de <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, e <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f901-106">Each child element represents a distinct attached property of <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span> <span data-ttu-id="6f901-107">Cada <xref:System.Windows.Controls.Button> está posicionado em relação ao pai <xref:System.Windows.Controls.Canvas> e de acordo com seu valor atribuído da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6f901-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6f901-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f901-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="6f901-109">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="6f901-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="6f901-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="6f901-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="6f901-111">Visão geral das propriedades anexadas</span><span class="sxs-lookup"><span data-stu-id="6f901-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
