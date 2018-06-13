---
title: Como fazer um objeto seguir o ponteiro do mouse
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 860b42f4dc068bc3063001e25e8b012c50b59213
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543866"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Como fazer um objeto seguir o ponteiro do mouse
Este exemplo mostra como alterar as dimensões de um objeto quando o ponteiro do mouse se move na tela.  
  
 O exemplo inclui um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo que cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e um arquivo de code-behind que cria o manipulador de eventos.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], que consiste um <xref:System.Windows.Shapes.Ellipse> dentro de um <xref:System.Windows.Controls.StackPanel>e anexa o manipulador de eventos para o <xref:System.Windows.UIElement.MouseMove> evento.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.MouseMove> manipulador de eventos.  Quando o ponteiro do mouse se move, a altura e a largura do <xref:System.Windows.Shapes.Ellipse> são aumentado e reduzido.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)
