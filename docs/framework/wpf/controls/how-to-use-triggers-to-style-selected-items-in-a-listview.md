---
title: 'Como: Usar gatilhos para criar itens selecionados em um ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 8c2d4adb2471c0f1891288573ce6b6460b20151d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367915"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Como: Usar gatilhos para criar itens selecionados em um ListView
Este exemplo mostra como definir <xref:System.Windows.Style.Triggers%2A> para um <xref:System.Windows.Controls.ListViewItem> controle, de modo que quando um valor de propriedade de um <xref:System.Windows.Controls.ListViewItem> alterações, o <xref:System.Windows.Style> do <xref:System.Windows.Controls.ListViewItem> alterações na resposta.  
  
## <a name="example"></a>Exemplo  
 Se você quiser que o <xref:System.Windows.Style> de um <xref:System.Windows.Controls.ListViewItem> para alterar em resposta às alterações de propriedade, defina <xref:System.Windows.Style.Triggers%2A> para o <xref:System.Windows.Style> alterar.  
  
 O exemplo a seguir define uma <xref:System.Windows.Trigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade <xref:System.Windows.Media.Brushes.Blue%2A> e altera o <xref:System.Windows.FrameworkElement.Cursor%2A> para exibir um <xref:System.Windows.Input.CursorType.Hand> quando o <xref:System.Windows.UIElement.IsMouseOver%2A> alteração na propriedade `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 O exemplo a seguir define uma <xref:System.Windows.MultiTrigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.ListViewItem> à <xref:System.Windows.Media.Brushes.Yellow%2A> quando o <xref:System.Windows.Controls.ListViewItem> é o item selecionado e tem o foco do teclado.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
