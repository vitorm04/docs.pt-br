---
title: 'Como: Usar um menu contextual personalizado com um TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: 805f5205a91f9b3da0c48c987f1f49f1d81892b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358594"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Como: Usar um menu contextual personalizado com um TextBox
Este exemplo mostra como definir e implementar um menu de contexto personalizado simples para um <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo define um <xref:System.Windows.Controls.TextBox> controle que inclui um menu de contexto.  
  
 O menu de contexto é definido usando um <xref:System.Windows.Controls.ContextMenu> elemento.  O menu de contexto consiste em uma série de <xref:System.Windows.Controls.MenuItem> elementos e <xref:System.Windows.Controls.Separator> elementos.  Cada <xref:System.Windows.Controls.MenuItem> elemento define um comando no menu de contexto; a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atributo define o texto exibido para o comando de menu e o <xref:System.Windows.Controls.MenuItem.Click> atributo especifica um método de manipulador para cada item de menu.  O <xref:System.Windows.Controls.Separator> simplesmente faz com que o elemento de uma linha de separação seja renderizada entre os itens de menu anterior e posterior.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código de implementação para a definição de menu de contexto anterior, bem como o código que habilita e desabilita o menu de contexto.  O <xref:System.Windows.Controls.ContextMenu.Opened> evento é usado para habilitar ou desabilitar determinados comandos dependendo do estado atual do dinamicamente o <xref:System.Windows.Controls.TextBox>.  
  
 Para restaurar o menu de contexto padrão, use o <xref:System.Windows.DependencyObject.ClearValue%2A> método para limpar o valor da <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade.  Para desabilitar completamente o menu de contexto, defina as <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade como uma referência nula (`Nothing` no Visual Basic).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Consulte também
- [Usar verificação ortográfica com um menu de contexto](how-to-use-spell-checking-with-a-context-menu.md)
- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
