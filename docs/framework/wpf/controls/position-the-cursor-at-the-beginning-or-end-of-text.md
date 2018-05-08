---
title: Como posicionar o cursor no início ou no término do texto em um controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 79ecf1d5dccee0dacef8e288c0c2e044334e65d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Como posicionar o cursor no início ou no término do texto em um controle TextBox
Este exemplo mostra como posicionar o cursor no início ou no final do conteúdo do texto de um <xref:System.Windows.Controls.TextBox> controle.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um <xref:System.Windows.Controls.TextBox> controlar e atribui a ela um nome.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Exemplo  
 Para posicionar o cursor no início do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especifique a seleção de posição de início 0 e o comprimento da seleção de 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Exemplo  
 Para posicionar o cursor no final do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especificar a posição de início de seleção para o comprimento do conteúdo texto e um comprimento de seleção de 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
