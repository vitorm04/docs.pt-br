---
title: Como criar um modo de exibição personalizado para um ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243213"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Como: Criar um modo de exibição personalizado para uma ListView

Este exemplo mostra como <xref:System.Windows.Controls.ListView.View%2A> criar um <xref:System.Windows.Controls.ListView> modo personalizado para um controle.  
  
## <a name="example"></a>Exemplo  
 Você deve <xref:System.Windows.Controls.ViewBase> usar a classe quando criar <xref:System.Windows.Controls.ListView> uma exibição personalizada para o controle. O exemplo a seguir `PlainView` mostra um modo de <xref:System.Windows.Controls.ViewBase> exibição chamado derivado da classe.  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Para aplicar um estilo à exibição personalizada, use a <xref:System.Windows.Style> classe. O exemplo a <xref:System.Windows.Style> seguir `PlainView` define um para o modo de exibição. No exemplo anterior, esse estilo é definido <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> como o valor `PlainView`da propriedade definida para .  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Para definir o layout dos dados em <xref:System.Windows.DataTemplate> um modo de exibição personalizado, defina um objeto. O exemplo a <xref:System.Windows.DataTemplate> seguir define um que pode `PlainView` ser usado para exibir dados no modo de exibição.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 O exemplo a seguir <xref:System.Windows.ResourceKey> mostra `PlainView` como definir um <xref:System.Windows.DataTemplate> modo de exibição que usa o que é definido no exemplo anterior.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Um <xref:System.Windows.Controls.ListView> controle pode usar uma exibição personalizada se você definir a <xref:System.Windows.Controls.ListView.View%2A> propriedade para a chave de recurso. O exemplo a seguir `PlainView` mostra como especificar como o modo de exibição para a <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Para obter a amostra completa, consulte [ListView com Múltiplas visualizações (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) ou [ListView com múltiplas visualizações (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
