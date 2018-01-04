---
title: Como fazer um objeto seguir o ponteiro do mouse
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
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7571b437c3879e829a11ed81c22dd12a0a1b592b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="4396c-102">Como fazer um objeto seguir o ponteiro do mouse</span><span class="sxs-lookup"><span data-stu-id="4396c-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="4396c-103">Este exemplo mostra como alterar as dimensões de um objeto quando o ponteiro do mouse se move na tela.</span><span class="sxs-lookup"><span data-stu-id="4396c-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="4396c-104">O exemplo inclui um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo que cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e um arquivo de code-behind que cria o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4396c-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4396c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4396c-105">Example</span></span>  
 <span data-ttu-id="4396c-106">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], que consiste um <xref:System.Windows.Shapes.Ellipse> dentro de um <xref:System.Windows.Controls.StackPanel>e anexa o manipulador de eventos para o <xref:System.Windows.UIElement.MouseMove> evento.</span><span class="sxs-lookup"><span data-stu-id="4396c-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="4396c-107">O código a seguir cria o <xref:System.Windows.UIElement.MouseMove> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4396c-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="4396c-108">Quando o ponteiro do mouse se move, a altura e a largura do <xref:System.Windows.Shapes.Ellipse> são aumentado e reduzido.</span><span class="sxs-lookup"><span data-stu-id="4396c-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="4396c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4396c-109">See Also</span></span>  
 [<span data-ttu-id="4396c-110">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="4396c-110">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
