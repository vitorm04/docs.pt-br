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
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107309"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Como: Fazer um objeto seguir o ponteiro do mouse
Este exemplo mostra como alterar as dimensões de um objeto quando o ponteiro do mouse se move na tela.  
  
 O exemplo inclui um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo que cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e um arquivo code-behind que cria o manipulador de eventos.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], que consiste em um <xref:System.Windows.Shapes.Ellipse> dentro de uma <xref:System.Windows.Controls.StackPanel>e anexa o manipulador de eventos para o <xref:System.Windows.UIElement.MouseMove> eventos.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 O código a seguir cria o <xref:System.Windows.UIElement.MouseMove> manipulador de eventos.  Quando o ponteiro do mouse se move, a altura e a largura do <xref:System.Windows.Shapes.Ellipse> são aumentado e reduzido.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da entrada](input-overview.md)
