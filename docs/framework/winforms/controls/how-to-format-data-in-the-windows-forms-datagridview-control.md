---
title: 'Como: Formatar dados no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 0f295b44bf1dfffc7f4b6c52b54705bba1d82a81
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609775"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Como: Formatar dados no controle DataGridView do Windows Forms
Os procedimentos a seguir demonstram a formatação básica de valores de célula usando a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade de um <xref:System.Windows.Forms.DataGridView> controle e de colunas específicas em um controle. Para obter informações sobre a formatação de dados avançados, consulte [como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Formatar os valores de moeda e datas  
  
- Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>. O exemplo de código a seguir define o formato para colunas específicas usando o <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade das colunas. Valores na coluna `UnitPrice` aparecem no formato de moeda específico da cultura atual, com valores negativos entre parênteses. Valores na coluna `ShipDate` aparecem no formato de data curto específico da cultura atual. Para obter mais informações sobre <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> valores, consulte [tipos de formatação](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Personalizar a exibição de valores nulos de banco de dados  
  
- Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para não exibir "nenhuma entrada" em todas as células que contêm valores iguais a <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Habilitar quebra automática de linha nas células de texto  
  
- Defina a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle> a um do <xref:System.Windows.Forms.DataGridViewTriState> valores de enumeração. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir o modo de encapsulamento para todo o controle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>Especificar o alinhamento de texto de células DataGridView  
  
- Defina a <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle> a um do <xref:System.Windows.Forms.DataGridViewContentAlignment> valores de enumeração. O exemplo de código a seguir define o alinhamento de uma coluna específica usando o <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade da coluna.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
- Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `UnitPrice`, uma coluna denominada `ShipDate`e uma coluna denominada `CustomerName`.  
  
- Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos em vez de configurar as propriedades de estilo para cada elemento separadamente. Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Formatando Tipos](../../../standard/base-types/formatting-types.md)
