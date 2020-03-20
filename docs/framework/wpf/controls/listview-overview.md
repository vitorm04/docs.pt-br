---
title: Visão geral de ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187515"
---
# <a name="listview-overview"></a>Visão geral de ListView
O <xref:System.Windows.Controls.ListView> controle fornece a infra-estrutura para exibir um conjunto de itens de dados em diferentes layouts ou visualizações. Por exemplo, talvez um usuário queira exibir itens de dados em uma tabela e classificar suas colunas.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>O que é uma ListView?  
 O <xref:System.Windows.Controls.ListView> controle <xref:System.Windows.Controls.ItemsControl> é um que <xref:System.Windows.Controls.ListBox>é derivado de . Normalmente, seus itens são membros de uma coleta <xref:System.Windows.Controls.ListViewItem> de dados e são representados como objetos. A <xref:System.Windows.Controls.ListViewItem> é <xref:System.Windows.Controls.ContentControl> um e pode conter apenas um único elemento filho. No entanto, esse elemento filho pode ser qualquer elemento visual.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Definindo um modo de exibição para um ListView  
 Para especificar um modo de <xref:System.Windows.Controls.ListView> exibição para <xref:System.Windows.Controls.ListView.View%2A> o conteúdo de um controle, você define a propriedade. Um modo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de <xref:System.Windows.Controls.GridView>exibição que fornece é , que exibe uma coleção de itens de dados em uma tabela que tem colunas personalizáveis.  
  
 O exemplo a seguir <xref:System.Windows.Controls.GridView> mostra <xref:System.Windows.Controls.ListView> como definir um controle que exibe as informações dos funcionários.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra como os dados são exibidos no exemplo anterior.  
  
 ![Captura de tela que mostra uma listView com saída GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Você pode criar um modo de exibição personalizado <xref:System.Windows.Controls.ViewBase> definindo uma classe que herda da classe. A <xref:System.Windows.Controls.ViewBase> classe fornece a infra-estrutura que você precisa para criar uma exibição personalizada. Para obter mais informações sobre como criar uma exibição personalizada, consulte [Criar um modo de exibição personalizado para um ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Associando dados a um ListView  
 Use <xref:System.Windows.Controls.ItemsControl.Items%2A> as <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedades e para especificar itens para um <xref:System.Windows.Controls.ListView> controle. O exemplo a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> seguir define a propriedade `EmployeeInfoDataSource`para uma coleta de dados chamada .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Em <xref:System.Windows.Controls.GridView>um <xref:System.Windows.Controls.GridViewColumn> , objetos se ligam a campos de dados especificados. O exemplo a <xref:System.Windows.Controls.GridViewColumn> seguir vincula um objeto <xref:System.Windows.Data.Binding> a <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> um campo de dados especificando um para a propriedade.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Você também pode <xref:System.Windows.Data.Binding> especificar <xref:System.Windows.DataTemplate> uma como parte de uma definição que você usa para estilizar as células em uma coluna. No exemplo a <xref:System.Windows.DataTemplate> seguir, o <xref:System.Windows.ResourceKey> que <xref:System.Windows.Data.Binding> é <xref:System.Windows.Controls.GridViewColumn>identificado com um conjunto para a . Observe que este exemplo <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> não define o porque fazê-lo substitui <xref:System.Windows.DataTemplate>a vinculação especificada por .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Estilizando uma ListView que implemente um GridView  
 O <xref:System.Windows.Controls.ListView> controle <xref:System.Windows.Controls.ListViewItem> contém objetos que representam os itens de dados exibidos. Você pode usar as propriedades a seguir para definir o conteúdo e estilo de itens de dados:  
  
- No <xref:System.Windows.Controls.ListView> controle, use <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>as <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> propriedades e as propriedades.  
  
- No <xref:System.Windows.Controls.ListViewItem> controle, use <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> as propriedades e.  
  
 Para evitar problemas de alinhamento <xref:System.Windows.Controls.GridView>entre células <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> em a, não use as propriedades de definir <xref:System.Windows.Controls.ListView>ou adicionar conteúdo que afete a largura de um item em um . Por exemplo, um problema de alinhamento <xref:System.Windows.FrameworkElement.Margin%2A> pode <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>ocorrer quando você define a propriedade no . Para especificar propriedades ou definir conteúdo que afete a largura dos itens em um <xref:System.Windows.Controls.GridView>, use as propriedades da <xref:System.Windows.Controls.GridView> classe e suas classes relacionadas, tais como <xref:System.Windows.Controls.GridViewColumn>.  
  
 Para obter mais informações <xref:System.Windows.Controls.GridView> sobre como usar e suas classes de suporte, consulte [GridView Overview](gridview-overview.md).  
  
 Se você <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> definir <xref:System.Windows.Controls.ListView> um para um <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>controle e <xref:System.Windows.Controls.ContentPresenter> também definir um , <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> você deve incluir um no estilo para que o trabalho funcione corretamente.  
  
 Não use <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> as <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriedades <xref:System.Windows.Controls.ListView> e propriedades para o <xref:System.Windows.Controls.GridView>conteúdo exibido usando um . Para especificar o alinhamento do <xref:System.Windows.Controls.GridView>conteúdo em <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>uma coluna de a, defina um .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Compartilhando o mesmo modo de exibição  
 Dois <xref:System.Windows.Controls.ListView> controles não podem compartilhar o mesmo modo de exibição ao mesmo tempo. Se você tentar usar o mesmo modo <xref:System.Windows.Controls.ListView> de exibição com mais de um controle, uma exceção ocorrerá.  
  
 Para especificar um modo de exibição que <xref:System.Windows.Controls.ListView>pode ser usado simultaneamente por mais de um , use modelos ou estilos.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Criando um modo de exibição personalizada  
 As visualizações <xref:System.Windows.Controls.GridView> personalizadas como <xref:System.Windows.Controls.ViewBase> são derivadas da classe abstrata, que fornece <xref:System.Windows.Controls.ListViewItem> as ferramentas para exibir itens de dados que são representados como objetos.
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [Visão geral de GridView](gridview-overview.md)
- [Tópicos de como fazer](listview-how-to-topics.md)
- [Controles](../advanced/optimizing-performance-controls.md)
