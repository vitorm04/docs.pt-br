---
title: DataGrid
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63eb1b7aec0c65192f67035fc7bc624fa1d2ae81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datagrid"></a>DataGrid
O <xref:System.Windows.Controls.DataGrid> controle permite que você exibir e editar dados de várias fontes diferentes, como de um banco de dados SQL, a consulta LINQ ou qualquer outra fonte de dados. Para obter mais informações, consulte [Visão geral de origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Colunas podem exibir texto, controles, como um <xref:System.Windows.Controls.ComboBox>, ou qualquer outro conteúdo do WPF, como imagens, botões ou qualquer conteúdo contido em um modelo. Você pode usar um <xref:System.Windows.Controls.DataGridTemplateColumn> para exibir os dados definidos em um modelo. A tabela a seguir lista os tipos de coluna fornecidos por padrão.  
  
|Tipo de coluna gerada|Tipo de dados|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>pode ser personalizado de aparência, como tamanho, cor e fonte da célula. <xref:System.Windows.Controls.DataGrid>oferece suporte a todas as funcionalidades de estilos e modelagem de outros controles do WPF. <xref:System.Windows.Controls.DataGrid>também inclui padrão e comportamentos personalizáveis para edição, classificação e a validação.  
  
 A tabela a seguir lista algumas das tarefas comuns para <xref:System.Windows.Controls.DataGrid> e como realizá-las. Ao exibir a API relacionada, você pode encontrar mais informações e o código de exemplo.  
  
|Cenário|Abordagem|  
|--------------|--------------|  
|Alternando as cores da tela de fundo|Definir o <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> propriedade para 2 ou maior e, em seguida, atribua um <xref:System.Windows.Media.Brush> para o <xref:System.Windows.Controls.DataGrid.RowBackground%2A> e <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> propriedades.|  
|Definir o comportamento da seleção de linha e de célula|Definir o <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> e <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> propriedades.|  
|Personalizar a aparência de cabeçalhos, células e linhas|Aplicar um novo <xref:System.Windows.Style> para o <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, ou <xref:System.Windows.Controls.DataGrid.RowStyle%2A> propriedades.|  
|Definir opções de dimensionamento|Definir o <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, ou <xref:System.Windows.FrameworkElement.MinWidth%2A> propriedades. Para obter mais informações, consulte [Opções de dimensionamento no controle DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Acessar itens selecionados|Verifique o <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> propriedade para obter as células selecionadas e <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> propriedade para obter as linhas selecionadas. Para obter mais informações, consulte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personalizar as interações do usuário final|Definir o <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, e <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> propriedades.|  
|Cancelar ou alterar colunas geradas automaticamente|Manipular o <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> evento.|  
|Congelar uma coluna|Definir o <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> propriedade para 1 e move a coluna para a posição mais à esquerda, definindo o <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> propriedade como 0.|  
|Usar dados XML como a fonte de dados|Associar o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> no <xref:System.Windows.Controls.DataGrid> para a consulta XPath que representa a coleção de itens. Criar cada coluna a <xref:System.Windows.Controls.DataGrid>. Associe cada coluna configurando o XPath na associação à consulta que obtém a propriedade na origem do item. Para ver um exemplo, consulte <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Passo a passo: exibir dados de um banco de dados do SQL Server em um controle DataGrid](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Descreve como configurar um novo projeto do WPF, adicionar um elemento de estrutura de entidade, defina a origem e exibir os dados em um <xref:System.Windows.Controls.DataGrid>.|  
|[Como adicionar detalhes de linha a um controle DataGrid](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Descreve como criar detalhes da linha para um <xref:System.Windows.Controls.DataGrid>.|  
|[Como implementar validação com o controle DataGrid](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Descreve como validar os valores em <xref:System.Windows.Controls.DataGrid> células e linhas e comentários de validação de exibição.|  
|[Comportamento padrão de teclado e mouse no controle DataGrid](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Descreve como interagir com o <xref:System.Windows.Controls.DataGrid> controle usando o teclado e mouse.|  
|[Como agrupar, classificar e filtrar dados no controle DataGrid](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Descreve como exibir dados em um <xref:System.Windows.Controls.DataGrid> de diferentes maneiras por agrupamento, classificação e filtragem dos dados.|  
|[Opções de dimensionamento no controle DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Descreve como controlar o dimensionamento absoluto e automática no <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.DataGrid>  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Controles](../../../../docs/framework/wpf/controls/index.md)  
 [Modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
