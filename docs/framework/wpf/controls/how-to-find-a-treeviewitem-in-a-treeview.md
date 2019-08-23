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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962088"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Como: Localizar um TreeViewItem em um TreeView
O <xref:System.Windows.Controls.TreeView> controle fornece uma maneira conveniente de exibir dados hierárquicos. Se o <xref:System.Windows.Controls.TreeView> estiver associado a uma fonte de dados, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> a propriedade fornecerá uma maneira conveniente para você recuperar rapidamente o objeto de dados selecionado. Normalmente, é melhor trabalhar com o objeto de dados subjacente, mas, às vezes, talvez seja necessário manipular programaticamente <xref:System.Windows.Controls.TreeViewItem>os dados que contêm. Por exemplo, talvez seja necessário expandir programaticamente <xref:System.Windows.Controls.TreeViewItem>o ou selecionar um item diferente <xref:System.Windows.Controls.TreeView>no.  
  
 Para localizar um <xref:System.Windows.Controls.TreeViewItem> que contenha um objeto <xref:System.Windows.Controls.TreeView>de dados específico, você deve percorrer cada nível do. Os itens em um <xref:System.Windows.Controls.TreeView> também podem ser virtualizados para melhorar o desempenho. No caso em que os itens podem ser virtualizados, você também deve perceber <xref:System.Windows.Controls.TreeViewItem> um para verificar se ele contém o objeto de dados.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir pesquisa <xref:System.Windows.Controls.TreeView> um para um objeto específico e retorna o recipiente <xref:System.Windows.Controls.TreeViewItem>do objeto. O exemplo garante que cada <xref:System.Windows.Controls.TreeViewItem> uma seja instanciada para que seus itens filho possam ser pesquisados. Este exemplo também funcionará se <xref:System.Windows.Controls.TreeView> o não usar itens virtualizados.  
  
> [!NOTE]
> O exemplo a seguir funciona para <xref:System.Windows.Controls.TreeView>qualquer, independentemente do modelo de dados subjacente e pesquisa a <xref:System.Windows.Controls.TreeViewItem> cada até que o objeto seja encontrado. Outra técnica que tem um melhor desempenho é Pesquisar o modelo de dados para o objeto especificado, controlar seu local dentro da hierarquia de dados e, em seguida, localizar <xref:System.Windows.Controls.TreeViewItem> o correspondente <xref:System.Windows.Controls.TreeView>no. No entanto, a técnica que tem melhor desempenho requer conhecimento do modelo de dados e não pode ser generalizada <xref:System.Windows.Controls.TreeView>para nenhum dado.  
  
## <a name="code"></a>Código  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 O código anterior se baseia em um personalizado <xref:System.Windows.Controls.VirtualizingStackPanel> que expõe um método chamado `BringIntoView`. O código a seguir define o <xref:System.Windows.Controls.VirtualizingStackPanel>personalizado.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 O XAML a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> que usa o personalizado <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Consulte também

- [Melhorar o desempenho de um TreeView](how-to-improve-the-performance-of-a-treeview.md)
