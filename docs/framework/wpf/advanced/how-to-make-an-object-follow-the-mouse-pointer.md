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
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005070"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Como: Fazer um objeto seguir o ponteiro do mouse
Este exemplo mostra como alterar as dimensões de um objeto quando o ponteiro do mouse se move na tela.  
  
 O exemplo inclui um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e um arquivo code-behind que cria o manipulador de eventos.  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], que consiste em um <xref:System.Windows.Shapes.Ellipse> dentro de um <xref:System.Windows.Controls.StackPanel> e anexa o manipulador de eventos ao evento <xref:System.Windows.UIElement.MouseMove>.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 O seguinte código por trás cria o manipulador de eventos <xref:System.Windows.UIElement.MouseMove>.  Quando o ponteiro do mouse se move, a altura e a largura do <xref:System.Windows.Shapes.Ellipse> são aumentadas e diminuídas.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da entrada](input-overview.md)
