---
title: Personalizar a formatação de dados no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746781"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Como personalizar a formatação de dados no controle DataGridView dos Windows Forms
O exemplo de código a seguir demonstra como implementar um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> que altera como as células são exibidas, dependendo de suas colunas e valores.  
  
 As células na coluna `Balance` que contêm números negativos recebem um plano de fundo vermelho. Você também pode formatar essas células como moeda para exibir parênteses em valores negativos. Para obter mais informações, consulte [Como formatar dados no controle DataGridView do Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 As células na coluna `Priority` exibem imagens no lugar de valores de células textuais correspondentes. A propriedade <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> da <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> é usada para obter o valor da célula textual e para definir o valor de exibição da imagem correspondente.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
- <xref:System.Drawing.Bitmap> imagens nomeadas `highPri.bmp`, `mediumPri.bmp`e `lowPri.bmp` que residem no mesmo diretório que o arquivo executável.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Exibindo dados no controle DataGridView dos Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como formatar dados no controle DataGridView dos Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Estilos de Célula no Controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
