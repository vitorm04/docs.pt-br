---
title: Visão geral do controle DataGrid
ms.date: 03/30/2017
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
ms.openlocfilehash: df559926dbc9141276f0a03deb99e340fd7212da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742570"
---
# <a name="datagrid-control-overview-windows-forms"></a>Visão geral do controle DataGrid (Windows Forms)

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

O controle de <xref:System.Windows.Forms.DataGrid> de Windows Forms exibe dados em uma série de linhas e colunas. O caso mais simples é quando a grade está associada a uma fonte de dados com uma única tabela que não contém relações. Nesse caso, os dados aparecem em linhas e colunas simples, como em uma planilha. Para obter mais informações sobre a vinculação de dados a outros controles, consulte [Vinculação de dados e Windows Forms](../data-binding-and-windows-forms.md).

Se a <xref:System.Windows.Forms.DataGrid> estiver associada a dados com várias tabelas relacionadas e se a navegação estiver habilitada na grade, a grade exibirá os expansores em cada linha. Com um expansor, o usuário pode se mover de uma tabela pai para uma tabela filho. A tabela filho é exibida ao clicar em um nó; a tabela pai original é exibida ao clicar em um botão Voltar. Dessa forma, a grade exibe as relações hierárquicas entre tabelas.

A captura de tela a seguir mostra um DataGrid associado a dados com várias tabelas:

![Um aplicativo WinForms que mostra um DataGrid associado a dados com várias tabelas.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

O <xref:System.Windows.Forms.DataGrid> pode fornecer uma interface do usuário para um conjunto de um, navegação entre tabelas relacionadas e recursos avançados de formatação e edição.

A exibição e a manipulação de dados são funções separadas: o controle manipula a interface do usuário, enquanto as atualizações de dados são manipuladas pela arquitetura de vinculação de dados Windows Forms e por .NET Framework provedores de dados. Portanto, vários controles associados à mesma fonte de dados permanecerão em sincronia.

> [!NOTE]
> Se você estiver familiarizado com o controle DataGrid no Visual Basic 6,0, encontrará algumas diferenças significativas no controle Windows Forms <xref:System.Windows.Forms.DataGrid>.

Quando a grade está associada a uma <xref:System.Data.DataSet>, as colunas e linhas são criadas automaticamente, formatadas e preenchidas. Para obter mais informações, consulte [Vinculação de dados e Windows Forms](../data-binding-and-windows-forms.md). Após a geração do controle de <xref:System.Windows.Forms.DataGrid>, você pode adicionar, excluir, reorganizar e Formatar colunas e linhas dependendo de suas necessidades.

## <a name="binding-data-to-the-control"></a>Associação de dados ao controle

Para que o controle de <xref:System.Windows.Forms.DataGrid> funcione, ele deve ser associado a uma fonte de dados usando as propriedades <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> em tempo de design ou o método <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> em tempo de execução. Essa associação aponta o <xref:System.Windows.Forms.DataGrid> para um objeto de fonte de dados instanciado, como um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>). O controle <xref:System.Windows.Forms.DataGrid> mostra os resultados das ações que são executadas nos dados. A maioria das ações específicas de dados não é executada por meio do <xref:System.Windows.Forms.DataGrid>, mas sim por meio da fonte de dados.

Se os dados no DataSet associado forem atualizados por meio de qualquer mecanismo, o controle de <xref:System.Windows.Forms.DataGrid> refletirá as alterações. Se a grade de dados e seus estilos de tabela e estilos de coluna tiverem a propriedade de `ReadOnly` definida como `false`, os dados no conjunto podem ser atualizados por meio do controle de <xref:System.Windows.Forms.DataGrid>.

Somente uma tabela pode ser mostrada no <xref:System.Windows.Forms.DataGrid> de cada vez. Se uma relação pai-filho for definida entre tabelas, o usuário poderá se mover entre as tabelas relacionadas para selecionar a tabela a ser exibida no controle de <xref:System.Windows.Forms.DataGrid>. Para obter informações sobre como associar um controle de <xref:System.Windows.Forms.DataGrid> a uma fonte de dados ADO.NET em tempo de design ou em tempo de execução, consulte [como associar o controle DataGrid de Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

As fontes de dados válidas para o <xref:System.Windows.Forms.DataGrid> incluem:

- Classe <xref:System.Data.DataTable>

- Classe <xref:System.Data.DataView>

- Classe <xref:System.Data.DataSet>

- Classe <xref:System.Data.DataViewManager>

Se a fonte for um conjunto de dados, ele poderá ser um objeto no formulário ou um objeto passado para o formulário por um serviço Web XML. É possível associar a conjuntos de dados tipados ou não tipados.

Você também pode associar um controle de <xref:System.Windows.Forms.DataGrid> a estruturas adicionais se os objetos na estrutura, como os elementos em uma matriz, expõem propriedades públicas. A grade exibirá todas as propriedades públicas dos elementos na estrutura. Por exemplo, se você associar o controle de <xref:System.Windows.Forms.DataGrid> a uma matriz de objetos Customer, a grade exibirá todas as propriedades públicas desses objetos Customer. Em alguns casos, isso significa que, apesar de ser possível associar à estrutura, a estrutura associada resultante poderá não ter aplicação prática. Você pode, por exemplo, associar a uma matriz de inteiros, mas, como o tipo de dados `Integer` não dá suporte a uma propriedade pública, a grade não consegue exibir nenhum dado.

Será possível se associar às estruturas a seguir se seus elementos expuserem propriedades públicas:

- Qualquer componente que implementa a interface <xref:System.Collections.IList>. Isso inclui matrizes de dimensão única.

- Qualquer componente que implementa a interface <xref:System.ComponentModel.IListSource>.

- Qualquer componente que implementa a interface <xref:System.ComponentModel.IBindingList>.

 Para obter mais informações sobre possíveis fontes de dados, consulte [Fontes de dados com suporte dos Windows Forms](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Exibição de grade

Um uso comum do controle de <xref:System.Windows.Forms.DataGrid> é exibir uma única tabela de dados a partir de um DataSet. No entanto, o controle também pode ser usado para exibir várias tabelas, incluindo tabelas relacionadas. A exibição da grade é ajustada automaticamente de acordo com a fonte de dados. A tabela a seguir mostra o que é exibido para várias configurações.

|Conteúdo do conjunto de dados|O que é exibido|
|--------------------------|-----------------------|
|Tabela única.|A tabela é exibida em uma grade.|
|Várias tabelas.|A grade pode exibir um modo de exibição de árvore em que os usuários podem navegar para localizar a tabela que desejam exibir.|
|Várias tabelas relacionadas.|A grade pode exibir um modo de exibição de árvore para selecionar tabelas ou é possível especificar para a grade exibir a tabela pai. Os registros na tabela pai permitem que os usuários naveguem até linhas filho relacionadas.|

> [!NOTE]
> As tabelas em um conjunto de um DataSet são relacionadas usando um <xref:System.Data.DataRelation>. Consulte também [criar relações entre conjuntos](/visualstudio/data-tools/relationships-in-datasets)de os.

Quando o controle de <xref:System.Windows.Forms.DataGrid> está exibindo uma tabela e a propriedade <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> é definida como `true`, os dados podem ser reclassificados clicando-se nos cabeçalhos de coluna. O usuário também pode adicionar linhas e editar células.

As relações entre um conjunto de tabelas são exibidas aos usuários por meio do uso de uma estrutura pai/filho de navegação. As tabelas pai são o nível mais alto de dados; as tabelas filho são as tabelas de dados derivadas de listagens de individuais nas tabelas pai. Os expansores são exibidos em cada linha pai que contém uma tabela filho. Ao clicar em um expansor, é gerada uma lista de links semelhantes a links Web para as tabelas filho. Quando o usuário seleciona um link, a tabela filho é exibida. Clicando no ícone Mostrar/Ocultar linhas pai (![Ícone Mostrar/Ocultar linhas pai](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) ocultará as informações sobre a tabela pai ou fará com que ela reapareça se o usuário a tiver ocultada anteriormente. O usuário pode clicar no botão Voltar para retornar à tabela visualizada anteriormente.

## <a name="columns-and-rows"></a>Colunas e linhas

O <xref:System.Windows.Forms.DataGrid> consiste em uma coleção de objetos <xref:System.Windows.Forms.DataGridTableStyle> que estão contidos na propriedade <xref:System.Windows.Forms.DataGrid.TableStyles%2A> do controle de <xref:System.Windows.Forms.DataGrid>. Um estilo de tabela pode conter uma coleção de objetos <xref:System.Windows.Forms.DataGridColumnStyle> contidos na propriedade <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> do <xref:System.Windows.Forms.DataGridTableStyle>.. Você pode editar as propriedades <xref:System.Windows.Forms.DataGrid.TableStyles%2A> e <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> usando editores de coleção acessados por meio da janela **Propriedades** .

Qualquer <xref:System.Windows.Forms.DataGridTableStyle> associado ao controle de <xref:System.Windows.Forms.DataGrid> pode ser acessado por meio do <xref:System.Windows.Forms.GridTableStylesCollection>. O <xref:System.Windows.Forms.GridTableStylesCollection> pode ser editado no designer com o editor de coleção <xref:System.Windows.Forms.DataGridTableStyle> ou programaticamente por meio da propriedade <xref:System.Windows.Forms.DataGrid.TableStyles%2A> do controle de <xref:System.Windows.Forms.DataGrid>.

A ilustração a seguir mostra os objetos incluídos no controle DataGrid:

![Diagrama que mostra objetos incluídos no controle DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Estilos de tabela e estilos de coluna são sincronizados com objetos <xref:System.Data.DataTable> e <xref:System.Data.DataColumn> objetos definindo suas propriedades `MappingName` para as propriedades apropriadas <xref:System.Data.DataTable.TableName%2A> e <xref:System.Data.DataColumn.ColumnName%2A>. Quando um <xref:System.Windows.Forms.DataGridTableStyle> que não tem estilos de coluna é adicionado a um controle de <xref:System.Windows.Forms.DataGrid> associado a uma fonte de dados válida, e a propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> desse estilo de tabela é definida como uma propriedade de <xref:System.Data.DataTable.TableName%2A> válida, uma coleção de objetos de <xref:System.Windows.Forms.DataGridColumnStyle> é criada para esse estilo de tabela. Para cada <xref:System.Data.DataColumn> encontrado na coleção <xref:System.Data.DataTable.Columns%2A> do <xref:System.Data.DataTable>, um <xref:System.Windows.Forms.DataGridColumnStyle> correspondente é adicionado à <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> é acessado por meio da propriedade <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> do <xref:System.Windows.Forms.DataGridTableStyle>. As colunas podem ser adicionadas ou excluídas da grade usando o método <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> ou <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> no <xref:System.Windows.Forms.GridColumnStylesCollection>. Para obter mais informações, consulte [Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) e [Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).

Uma coleção de tipos de coluna estende a classe <xref:System.Windows.Forms.DataGridColumnStyle> com recursos avançados de formatação e edição. Todos os tipos de coluna herdam da classe base <xref:System.Windows.Forms.DataGridColumnStyle>. A classe criada depende da propriedade <xref:System.Data.DataColumn.DataType%2A> da <xref:System.Data.DataColumn> da qual o <xref:System.Web.UI.WebControls.DataGridColumn> se baseia. Por exemplo, um <xref:System.Data.DataColumn> que tem sua propriedade <xref:System.Data.DataColumn.DataType%2A> definida como <xref:System.Boolean> será associado à <xref:System.Windows.Forms.DataGridBoolColumn>. A tabela a seguir descreve cada um desses tipos de coluna.

|Tipo de coluna|Descrição|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Aceita e exibe os dados como cadeias de caracteres formatadas ou não formatadas. Os recursos de edição são os mesmos que são para editar dados em um <xref:System.Windows.Forms.TextBox>simples. Herda de <xref:System.Windows.Forms.DataGridColumnStyle>.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|Aceita e exibe `true`, `false` e valores nulos. Herda de <xref:System.Windows.Forms.DataGridColumnStyle>.|

Ao clicar duas vezes na borda direita de uma coluna, a coluna é redimensionada para exibir a legenda completa e a maior entrada.

## <a name="table-styles-and-column-styles"></a>Estilos de tabela e de coluna

Assim que você tiver estabelecido o formato padrão do controle de <xref:System.Windows.Forms.DataGrid>, poderá personalizar as cores que serão usadas quando determinadas tabelas forem exibidas na grade de dados.

Isso é obtido com a criação de instâncias da classe <xref:System.Windows.Forms.DataGridTableStyle>. Os estilos de tabela especificam a formatação de tabelas específicas, diferentes da formatação padrão do próprio controle de <xref:System.Windows.Forms.DataGrid>. Cada tabela poderá ter apenas um estilo de tabela definido para ela de cada vez.

Às vezes, queremos que uma coluna específica tenha uma aparência diferente do restante das colunas de uma tabela de dados específica. Você pode criar um conjunto personalizado de estilos de coluna usando a propriedade <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

Os estilos de coluna estão relacionados às colunas em um conjunto de dados, assim como os estilos de tabelas estão relacionados às tabelas de dados. Assim como cada tabela poderá ter apenas um estilo de tabela definido para ela por vez, cada coluna poderá ter apenas um estilo de coluna definido para ela, em um estilo de tabela específico. Essa relação é definida na propriedade <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> da coluna.

Se você tiver criado um estilo de tabela sem estilos de coluna adicionados a ele, o Visual Studio adicionará os estilos de coluna padrão quando o formulário e a grade forem criados em tempo de execução. No entanto, se você tiver criado um estilo de tabela e adicionado quaisquer estilos de coluna a ele, o Visual Studio não criará nenhum estilo de coluna. Além disso, será necessário definir estilos de coluna e atribuí-los com o nome de mapeamento para que as colunas desejadas sejam exibidas na grade.

Como as colunas que serão incluídas na grade de dados são especificadas por meio da atribuição de um estilo de coluna e como nenhum estilo de coluna foi atribuído às colunas, é possível incluir colunas de dados no conjunto de dados que não são exibidas na grade. Porém, já que a coluna de dados está incluída no conjunto de dados, os dados não exibidos podem ser editados programaticamente.

> [!NOTE]
> Em geral, crie estilos de coluna e adicione-os à coleção de estilos de coluna antes de adicionar os estilos de tabela à coleção de estilos de tabela. Quando você adiciona um estilo de tabela vazio à coleção, os estilos de coluna são gerados automaticamente. Consequentemente, uma exceção será gerada se você tentar adicionar novos estilos de coluna com valores de <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> duplicados à coleção de estilos de coluna.
>
> Às vezes, será necessário ajustar somente uma coluna entre muitas colunas; por exemplo, o conjunto de dados contém 50 colunas e você quer apenas 49. Nesse caso, é mais fácil importar as 50 colunas e remover uma programaticamente, em vez de adicionar programaticamente cada uma das 49 colunas individuais desejadas.

## <a name="formatting"></a>Formatação

A formatação que pode ser aplicada ao controle de <xref:System.Windows.Forms.DataGrid> inclui estilos de borda, estilos de linha de grade, fontes, propriedades de legendas, alinhamento de dados e cores de plano de fundo alternadas entre linhas. Para obter mais informações, consulte [Como formatar o controle DataGrid dos Windows Forms](how-to-format-the-windows-forms-datagrid-control.md).

## <a name="events"></a>Events

Além dos eventos de controle comuns, como <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>e <xref:System.Windows.Forms.DataGrid.Scroll>, o controle de <xref:System.Windows.Forms.DataGrid> dá suporte a eventos associados à edição e navegação dentro da grade. A propriedade <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> determina qual célula está selecionada. O evento <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> é gerado quando o usuário navega para uma nova célula. Quando o usuário navega para uma nova tabela por meio de relações pai/filho, o evento <xref:System.Windows.Forms.DataGrid.Navigate> é gerado. O evento <xref:System.Windows.Forms.DataGrid.BackButtonClick> é gerado quando o usuário clica no botão voltar quando o usuário está exibindo uma tabela filho e o evento <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> é gerado quando o ícone Mostrar/Ocultar linhas pai é clicado.

## <a name="see-also"></a>Veja também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Como associar o controle DataGrid do Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Como formatar o controle DataGrid do Windows Forms](how-to-format-the-windows-forms-datagrid-control.md)
