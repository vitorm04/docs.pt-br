---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646127"
---
# <a name="datagrid"></a>DataGrid
O <xref:System.Windows.Controls.DataGrid> controle permite que você exiba e edite dados de muitas fontes diferentes, como a partir de um banco de dados SQL, consulta LINQ ou qualquer outra fonte de dados vinculável. Para obter mais informações, consulte [Visão geral de origens da associação](../data/binding-sources-overview.md).  
  
 As colunas podem exibir texto, <xref:System.Windows.Controls.ComboBox>controles, como um ou qualquer outro conteúdo do WPF, como imagens, botões ou qualquer conteúdo contido em um modelo. Você pode <xref:System.Windows.Controls.DataGridTemplateColumn> usar um para exibir dados definidos em um modelo. A tabela a seguir lista os tipos de coluna fornecidos por padrão.  
  
|Tipo de coluna gerada|Tipo de Dados|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>pode ser personalizado na aparência, como fonte de célula, cor e tamanho. <xref:System.Windows.Controls.DataGrid>suporta todas as funcionalidades de estilo e templating de outros controles WPF. <xref:System.Windows.Controls.DataGrid>também inclui comportamentos padrão e personalizáveis para edição, classificação e validação.  
  
 A tabela a seguir lista <xref:System.Windows.Controls.DataGrid> algumas das tarefas comuns para e como realizá-las. Ao exibir a API relacionada, você pode encontrar mais informações e o código de exemplo.  
  
|Cenário|Abordagem|  
|--------------|--------------|  
|Alternando as cores da tela de fundo|Defina <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> a propriedade como 2 ou <xref:System.Windows.Media.Brush> mais <xref:System.Windows.Controls.DataGrid.RowBackground%2A> e, em seguida, atribua um às propriedades. <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>|  
|Definir o comportamento da seleção de linha e de célula|Definir as propriedades <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> e <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personalizar a aparência de cabeçalhos, células e linhas|Aplique um <xref:System.Windows.Style> novo <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>nas <xref:System.Windows.Controls.DataGrid.CellStyle%2A>propriedades, ou <xref:System.Windows.Controls.DataGrid.RowStyle%2A> propriedades.|  
|Definir opções de dimensionamento|Defina <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A>as <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MinWidth%2A> propriedades, ou propriedades. Para obter mais informações, consulte [Opções de dimensionamento no controle DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Acessar itens selecionados|Verifique <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> a propriedade para obter as <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> células selecionadas e a propriedade para obter as linhas selecionadas. Para obter mais informações, consulte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personalizar as interações do usuário final|Defina <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>as <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> propriedades e as propriedades.|  
|Cancelar ou alterar colunas geradas automaticamente|Cuide <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> do evento.|  
|Congelar uma coluna|Defina <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> a propriedade como 1 e mova a coluna <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> para a posição mais à esquerda, definindo a propriedade como 0.|  
|Usar dados XML como a fonte de dados|Vincule <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> o <xref:System.Windows.Controls.DataGrid> no na consulta XPath que representa a coleção de itens. Crie cada coluna <xref:System.Windows.Controls.DataGrid>no . Associe cada coluna configurando o XPath na associação à consulta que obtém a propriedade na origem do item. Para ver um exemplo, consulte <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tópicos Relacionados  
  
|Title|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: exibir dados a partir de um banco de dados do SQL Server em um controle DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Descreve como configurar um novo projeto WPF, adicionar um Elemento Framework de Entidade, <xref:System.Windows.Controls.DataGrid>definir a origem e exibir os dados em um .|  
|[Como adicionar detalhes de linha a um controle DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Descreve como criar detalhes <xref:System.Windows.Controls.DataGrid>de linha para um .|  
|[Como implementar validação com o controle DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Descreve como validar <xref:System.Windows.Controls.DataGrid> valores em células e linhas e exibir feedback de validação.|  
|[Teclado padrão e comportamento do mouse no controle DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Descreve como interagir com <xref:System.Windows.Controls.DataGrid> o controle usando o teclado e o mouse.|  
|[Como agrupar, classificar e filtrar dados no controle DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Descreve como visualizar dados <xref:System.Windows.Controls.DataGrid> de uma forma diferente, agrupando, classificando e filtrando os dados.|  
|[Opções de dimensionamento no controle DataGrid](sizing-options-in-the-datagrid-control.md)|Descreve como controlar o dimensionamento absoluto <xref:System.Windows.Controls.DataGrid>e automático no .|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.DataGrid>
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](../data/data-templating-overview.md)
- [Controles](index.md)
- [Modelo de conteúdo do WPF](wpf-content-model.md)
