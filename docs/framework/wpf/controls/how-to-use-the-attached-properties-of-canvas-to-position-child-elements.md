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
ms.openlocfilehash: 89327b834dfd71c0a7420eb42a598b98cdb5e9d8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513395"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="795c1-102">Como usar as propriedades anexas de tela para posicionar elementos filho</span><span class="sxs-lookup"><span data-stu-id="795c1-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="795c1-103">Este exemplo mostra como usar as propriedades anexas de <xref:System.Windows.Controls.Canvas> para posicionar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="795c1-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="795c1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="795c1-104">Example</span></span>  
 <span data-ttu-id="795c1-105">O exemplo a seguir adiciona quatro <xref:System.Windows.Controls.Button> elementos como elementos filho de um pai <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="795c1-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="795c1-106">Cada elemento é representado por um <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, e <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="795c1-106">Each element is represented by a <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span>
<span data-ttu-id="795c1-107">Cada <xref:System.Windows.Controls.Button> é posicionado em relação ao pai <xref:System.Windows.Controls.Canvas> e de acordo com seu valor atribuído da propriedade.</span><span class="sxs-lookup"><span data-stu-id="795c1-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="795c1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="795c1-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="795c1-109">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="795c1-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="795c1-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="795c1-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="795c1-111">Visão geral das propriedades anexadas</span><span class="sxs-lookup"><span data-stu-id="795c1-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
