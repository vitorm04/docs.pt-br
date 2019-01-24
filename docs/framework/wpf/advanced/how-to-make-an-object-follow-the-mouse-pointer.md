---
title: 'Como: Fazer um objeto seguir o ponteiro do mouse'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 3e39b9459fbc94c9b7684ffd7c597363e46ad717
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541814"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="f2c7d-102">Como: Fazer um objeto seguir o ponteiro do mouse</span><span class="sxs-lookup"><span data-stu-id="f2c7d-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="f2c7d-103">Este exemplo mostra como alterar as dimensões de um objeto quando o ponteiro do mouse se move na tela.</span><span class="sxs-lookup"><span data-stu-id="f2c7d-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="f2c7d-104">O exemplo inclui um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo que cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e um arquivo code-behind que cria o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f2c7d-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2c7d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2c7d-105">Example</span></span>  
 <span data-ttu-id="f2c7d-106">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], que consiste em um <xref:System.Windows.Shapes.Ellipse> dentro de uma <xref:System.Windows.Controls.StackPanel>e anexa o manipulador de eventos para o <xref:System.Windows.UIElement.MouseMove> eventos.</span><span class="sxs-lookup"><span data-stu-id="f2c7d-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="f2c7d-107">O código a seguir cria o <xref:System.Windows.UIElement.MouseMove> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f2c7d-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="f2c7d-108">Quando o ponteiro do mouse se move, a altura e a largura do <xref:System.Windows.Shapes.Ellipse> são aumentado e reduzido.</span><span class="sxs-lookup"><span data-stu-id="f2c7d-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="f2c7d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2c7d-109">See also</span></span>
- [<span data-ttu-id="f2c7d-110">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="f2c7d-110">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
