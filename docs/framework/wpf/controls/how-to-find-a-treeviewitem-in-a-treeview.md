---
title: 'Como: Localizar um TreeViewItem em um TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: c90db5312d58cfba18910f299386e2884fb36ce6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360207"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Como: Localizar um TreeViewItem em um TreeView
O <xref:System.Windows.Controls.TreeView> controle fornece uma maneira conveniente de exibir dados hierárquicos. Se sua <xref:System.Windows.Controls.TreeView> está associado a uma fonte de dados, o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade fornece uma maneira conveniente para que você possa recuperar rapidamente o objeto de dados selecionado. É geralmente a melhor trabalhar com o objeto de dados subjacente, mas, às vezes, talvez você precise manipular programaticamente os dados que contém <xref:System.Windows.Controls.TreeViewItem>. Por exemplo, talvez você precise expandir programaticamente o <xref:System.Windows.Controls.TreeViewItem>, ou selecione um item diferente no <xref:System.Windows.Controls.TreeView>.  
  
 Para localizar um <xref:System.Windows.Controls.TreeViewItem> que contém um objeto de dados específico, você deve percorrer cada nível do <xref:System.Windows.Controls.TreeView>. Os itens em um <xref:System.Windows.Controls.TreeView> também podem ser virtualizados para melhorar o desempenho. No caso em que os itens podem ser virtualizados, você também deverá efetuar um <xref:System.Windows.Controls.TreeViewItem> para verificar se ele contém o objeto de dados.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
 O exemplo seguinte pesquisa uma <xref:System.Windows.Controls.TreeView> para um objeto específico e retorna o objeto que contém <xref:System.Windows.Controls.TreeViewItem>. O exemplo garante que cada <xref:System.Windows.Controls.TreeViewItem> é instanciado para que seus itens filho podem ser pesquisados. Este exemplo também funciona se o <xref:System.Windows.Controls.TreeView> usar itens virtualizados.  
  
> [!NOTE]
>  O exemplo a seguir funciona para qualquer <xref:System.Windows.Controls.TreeView>, independentemente do modelo de dados subjacente e pesquisas cada <xref:System.Windows.Controls.TreeViewItem> até que o objeto for encontrado. Outra técnica que apresenta melhor desempenho é pesquisar o modelo de dados para o objeto especificado, manter o controle de seu local dentro da hierarquia de dados e, em seguida, localizar correspondente <xref:System.Windows.Controls.TreeViewItem> no <xref:System.Windows.Controls.TreeView>. No entanto, a técnica que apresenta melhor desempenho requer conhecimento sobre o modelo de dados e não pode ser generalizada para qualquer dado <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Código  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 O código anterior se baseia em um personalizado <xref:System.Windows.Controls.VirtualizingStackPanel> que expõe um método chamado `BringIntoView`. O código a seguir define personalizado <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 O XAML a seguir mostra como criar uma <xref:System.Windows.Controls.TreeView> que usa o personalizado <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Consulte também
- [Melhorar o desempenho de um TreeView](how-to-improve-the-performance-of-a-treeview.md)
