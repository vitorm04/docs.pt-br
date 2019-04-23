---
title: Personalizando o controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: ab8d1f07c608aca4f14f5e73860f8c3e263a4610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091376"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Personalizando o controle DataGridView dos Windows Forms
O controle `DataGridView` fornece várias propriedades que podem ser usadas para ajustar a aparência e o comportamento básico (visual) das células, linhas e colunas. Se você tiver necessidades especiais que vão além dos recursos da <xref:System.Windows.Forms.DataGridViewCellStyle> de classe, no entanto, você também pode implementar o desenho do proprietário para o controle ou estender seus recursos criando células personalizadas, colunas e linhas.  
  
 Para pintar linhas e células por conta própria, você pode manipular vários eventos de pintura `DataGridView`. Para modificar a funcionalidade existente ou fornecer novas funcionalidades, crie seus próprios tipos derivados dos tipos `DataGridViewCell`, `DataGridViewColumn` e `DataGridViewRow` existentes. Você também pode fornecer novos recursos de edição criando tipos derivados que exibem um controle de sua escolha quando uma célula está em modo de edição.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Descreve como manipular o <xref:System.Windows.Forms.DataGridView.CellPainting> evento para pintar células manualmente.  
  
 [Como: Personalizar a aparência das linhas no controle DataGridView dos Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Descreve como lidar com o <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> eventos para pintar linhas com uma tela de fundo gradiente personalizada e de conteúdo que se estende por várias colunas.  
  
 [Como: Personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e aparência](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Descreve como criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para realçar células ao posicionar o ponteiro do mouse sobre elas.  
  
 [Como: Desabilitar botões em uma coluna de botão no controle DataGridView dos Windows Forms](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Descreve como criar tipos personalizados derivados de <xref:System.Windows.Forms.DataGridViewButtonCell> e <xref:System.Windows.Forms.DataGridViewButtonColumn> para exibir botões desabilitados em uma coluna de botão.  
  
 [Como: Hospedar controles em células de DataGridView dos Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Descreve como implementar o `IDataGridViewEditingControl` da interface e criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para exibir um <xref:System.Windows.Forms.DateTimePicker> controlar quando uma célula está no modo de edição.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DataGridView>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewCell> classe.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewRow> classe.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumn> classe.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.  
  
## <a name="see-also"></a>Consulte também

- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
