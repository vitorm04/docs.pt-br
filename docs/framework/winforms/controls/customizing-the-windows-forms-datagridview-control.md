---
title: Personalizar controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744026"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Personalizando o controle DataGridView dos Windows Forms
O controle `DataGridView` fornece várias propriedades que podem ser usadas para ajustar a aparência e o comportamento básico (visual) das células, linhas e colunas. No entanto, se você tiver necessidades especiais que vão além dos recursos da classe <xref:System.Windows.Forms.DataGridViewCellStyle>, também poderá implementar o desenho do proprietário para o controle ou estender seus recursos Criando células, colunas e linhas personalizadas.  
  
 Para pintar linhas e células por conta própria, você pode manipular vários eventos de pintura `DataGridView`. Para modificar a funcionalidade existente ou fornecer novas funcionalidades, crie seus próprios tipos derivados dos tipos `DataGridViewCell`, `DataGridViewColumn` e `DataGridViewRow` existentes. Você também pode fornecer novos recursos de edição criando tipos derivados que exibem um controle de sua escolha quando uma célula está em modo de edição.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Descreve como manipular o evento <xref:System.Windows.Forms.DataGridView.CellPainting> para pintar células manualmente.  
  
 [Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Descreve como lidar com os eventos <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> para pintar linhas com um plano de fundo personalizado, gradiente e conteúdo que abrange várias colunas.  
  
 [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Descreve como criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para realçar células ao posicionar o ponteiro do mouse sobre elas.  
  
 [Como desabilitar botões em uma coluna de botão no controle DataGridView dos Windows Forms](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Descreve como criar tipos personalizados derivados de <xref:System.Windows.Forms.DataGridViewButtonCell> e <xref:System.Windows.Forms.DataGridViewButtonColumn> para exibir botões desabilitados em uma coluna de botão.  
  
 [Como hospedar controles em células DataGridView dos Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Descreve como implementar a interface `IDataGridViewEditingControl` e criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para exibir um controle de <xref:System.Windows.Forms.DateTimePicker> quando uma célula estiver no modo de edição.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DataGridView>  
 Fornece documentação de referência para o controle de <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewCell>.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewRow>.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Fornece documentação de referência para a interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.  
  
## <a name="see-also"></a>Veja também

- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
