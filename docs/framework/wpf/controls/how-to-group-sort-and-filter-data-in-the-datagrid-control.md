---
title: Como agrupar, classificar e filtrar dados no controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 2632566b5b55ae641d2750e903bf94cdc681f8f8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460243"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Como agrupar, classificar e filtrar dados no controle DataGrid

Geralmente, é útil exibir dados de uma <xref:System.Windows.Controls.DataGrid> de maneiras diferentes, agrupando, classificando e filtrando os dados. Para agrupar, classificar e filtrar os dados em um <xref:System.Windows.Controls.DataGrid>, vincule-os a uma <xref:System.Windows.Data.CollectionView> que ofereça suporte a essas funções. Em seguida, você pode trabalhar com os dados na <xref:System.Windows.Data.CollectionView> sem afetar os dados de origem subjacentes. As alterações na exibição de coleção são refletidas na interface do usuário do <xref:System.Windows.Controls.DataGrid> (UI).

A classe <xref:System.Windows.Data.CollectionView> fornece funcionalidade de agrupamento e classificação para uma fonte de dados que implementa a interface <xref:System.Collections.IEnumerable>. A classe <xref:System.Windows.Data.CollectionViewSource> permite que você defina as propriedades de um <xref:System.Windows.Data.CollectionView> de XAML.

Neste exemplo, uma coleção de objetos `Task` está associada a um <xref:System.Windows.Data.CollectionViewSource>. O <xref:System.Windows.Data.CollectionViewSource> é usado como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.DataGrid>. O agrupamento, a classificação e a filtragem são executados no <xref:System.Windows.Data.CollectionViewSource> e são exibidos na interface do usuário do <xref:System.Windows.Controls.DataGrid>.

![Dados agrupados em um DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Dados agrupados em um DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Usando um CollectionViewSource como ItemsSource

Para agrupar, classificar e filtrar dados em um controle de <xref:System.Windows.Controls.DataGrid>, vincule o <xref:System.Windows.Controls.DataGrid> a uma <xref:System.Windows.Data.CollectionView> que ofereça suporte a essas funções. Neste exemplo, a <xref:System.Windows.Controls.DataGrid> está associada a uma <xref:System.Windows.Data.CollectionViewSource> que fornece essas funções para uma <xref:System.Collections.Generic.List%601> de objetos `Task`.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Para associar um DataGrid a um CollectionViewSource

1. Crie uma coleta de dados que implementa a interface <xref:System.Collections.IEnumerable>.

    Se você usar <xref:System.Collections.Generic.List%601> para criar sua coleção, deverá criar uma nova classe que herda de <xref:System.Collections.Generic.List%601> em vez de instanciar uma instância do <xref:System.Collections.Generic.List%601>. Isso permite associar dados à coleção em XAML.

    > [!NOTE]
    > Os objetos na coleção devem implementar a interface <xref:System.ComponentModel.INotifyPropertyChanged> alterada e a interface <xref:System.ComponentModel.IEditableObject> para que o <xref:System.Windows.Controls.DataGrid> responda corretamente às alterações e edições de propriedade. Para obter mais informações, consulte [Implementar notificação de alteração da propriedade](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. No XAML, crie uma instância da classe de coleção e defina a [Diretiva x:Key](../../xaml-services/x-key-directive.md).

3. Em XAML, crie uma instância da classe <xref:System.Windows.Data.CollectionViewSource>, defina a [diretiva x:Key](../../xaml-services/x-key-directive.md)e defina a instância da sua classe de coleção como a <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Crie uma instância da classe <xref:System.Windows.Controls.DataGrid> e defina a propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> como a <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Para acessar o <xref:System.Windows.Data.CollectionViewSource> do seu código, use o método <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> para obter uma referência à <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Agrupando itens em um DataGrid

Para especificar como os itens são agrupados em um <xref:System.Windows.Controls.DataGrid>, use o tipo de <xref:System.Windows.Data.PropertyGroupDescription> para agrupar os itens na exibição de origem.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Para agrupar itens em um DataGrid usando XAML

1. Crie um <xref:System.Windows.Data.PropertyGroupDescription> que especifica a propriedade a ser agrupada. Você pode especificar a propriedade no XAML ou no código.

   1. Em XAML, defina o <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> como o nome da propriedade a ser agrupada.

   2. No código, passe o nome da propriedade segundo a qual o agrupamento será feito ao construtor.

2. Adicione o <xref:System.Windows.Data.PropertyGroupDescription> à coleção de <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>.

3. Adicione instâncias adicionais do <xref:System.Windows.Data.PropertyGroupDescription> à coleção de <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> para adicionar mais níveis de agrupamento.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Para remover um grupo, remova o <xref:System.Windows.Data.PropertyGroupDescription> da coleção de <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.

5. Para remover todos os grupos, chame o método <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> da coleção <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Quando os itens são agrupados na <xref:System.Windows.Controls.DataGrid>, você pode definir um <xref:System.Windows.Controls.GroupStyle> que especifica a aparência de cada grupo. Você aplica o <xref:System.Windows.Controls.GroupStyle> adicionando-o à coleção <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> do DataGrid. Se tiver vários níveis de agrupamento, você poderá aplicar estilos diferentes a cada nível de grupo. Os estilos são aplicados na ordem em que são definidos. Por exemplo, se você definir dois estilos, o primeiro será aplicado a grupos de linhas de nível superior. O segundo estilo será aplicado a todos os grupos de linhas no segundo nível e abaixo. A <xref:System.Windows.FrameworkElement.DataContext%2A> da <xref:System.Windows.Controls.GroupStyle> é a <xref:System.Windows.Data.CollectionViewGroup> que o grupo representa.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Para alterar a aparência dos cabeçalhos de grupos de linhas

1. Crie um <xref:System.Windows.Controls.GroupStyle> que define a aparência do grupo de linhas.

2. Coloque o <xref:System.Windows.Controls.GroupStyle> dentro das marcas de `<DataGrid.GroupStyle>`.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Classificando itens em um DataGrid

Para especificar como os itens são classificados em um <xref:System.Windows.Controls.DataGrid>, use o tipo de <xref:System.ComponentModel.SortDescription> para classificar os itens na exibição de origem.

### <a name="to-sort-items-in-a-datagrid"></a>Para classificar itens em um DataGrid

1. Crie um <xref:System.ComponentModel.SortDescription> que especifica a propriedade pela qual classificar. Você pode especificar a propriedade no XAML ou no código.

    1. Em XAML, defina o <xref:System.ComponentModel.SortDescription.PropertyName%2A> como o nome da propriedade pela qual classificar.

    2. No código, passe o nome da propriedade para classificar e a <xref:System.ComponentModel.ListSortDirection> para o construtor.

2. Adicione o <xref:System.ComponentModel.SortDescription> à coleção de <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>.

3. Adicione instâncias adicionais do <xref:System.ComponentModel.SortDescription> à coleção de <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> para classificar por propriedades adicionais.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrando itens em um DataGrid

Para filtrar itens em um <xref:System.Windows.Controls.DataGrid> usando uma <xref:System.Windows.Data.CollectionViewSource>, você fornece a lógica de filtragem no manipulador para o evento de <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

### <a name="to-filter-items-in-a-datagrid"></a>Para filtrar itens em um DataGrid

1. Adicione um manipulador para o evento <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

2. No manipulador de eventos <xref:System.Windows.Data.CollectionViewSource.Filter>, defina a lógica de filtragem.

    O filtro será aplicado sempre que a exibição for atualizada.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Como alternativa, você pode filtrar itens em um <xref:System.Windows.Controls.DataGrid> criando um método que fornece a lógica de filtragem e definindo a propriedade <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> para aplicar o filtro. Para ver um exemplo desse método, consulte [Filtrar dados em uma exibição](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como agrupar, classificar e filtrar `Task` dados em um <xref:System.Windows.Data.CollectionViewSource> e exibir os dados de `Task` agrupados, classificados e filtrados em um <xref:System.Windows.Controls.DataGrid>. O <xref:System.Windows.Data.CollectionViewSource> é usado como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.DataGrid>. O agrupamento, a classificação e a filtragem são executados no <xref:System.Windows.Data.CollectionViewSource> e são exibidos na interface do usuário do <xref:System.Windows.Controls.DataGrid>.

Para testar este exemplo, você precisará ajustar o nome de DGGroupSortFilterExample para corresponder ao nome do seu projeto. Se você estiver usando Visual Basic, será necessário alterar o nome da classe para <xref:System.Windows.Window> para o seguinte.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Criar e associar a um ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrar dados em uma exibição](../data/how-to-filter-data-in-a-view.md)
- [Classificar dados em uma exibição](../data/how-to-sort-data-in-a-view.md)
- [Classificar e agrupar dados usando uma exibição em XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
