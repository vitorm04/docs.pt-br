---
title: Formatação de dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: b5c055bdd12a4bede6e77233726c697de424a055
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158633"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatação de dados no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle fornece conversão automática entre os valores de célula e os tipos de dados que as colunas pai exibem. Colunas da caixa de texto, por exemplo, exibem representações de valores de data, hora, número e enumeração, e convertem valores de cadeia de caracteres inseridos pelo usuário nos tipos necessários para o armazenamento de dados.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatação com a classe DataGridViewCellStyle  
 O <xref:System.Windows.Forms.DataGridView> controle fornece dados básicos de formatação de valores de célula por meio de <xref:System.Windows.Forms.DataGridViewCellStyle> classe. Você pode usar o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade para formatar valores de data, hora, número e enumeração para a cultura padrão atual usando especificadores de formato descritos [tipos de formatação](../../../standard/base-types/formatting-types.md). Você também pode formatar esses valores para culturas específicas usando o <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> propriedade. O formato especificado é usado para exibir dados e analisar dados digitados pelo usuário no formato especificado.  
  
 O <xref:System.Windows.Forms.DataGridViewCellStyle> classe fornece propriedades adicionais de formatação para quebra automática de linha, alinhamento de texto e a exibição personalizada de valores nulos de banco de dados. Para obter mais informações, confira [Como: Formatar dados no Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatação com o evento CellFormatting  
 Se a formatação básica não atender às suas necessidades, você pode fornecer dados personalizados de formatação em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> eventos. O <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passado para o manipulador tem um <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade que inicialmente contém o valor da célula. Normalmente, esse valor é automaticamente convertido no tipo de exibição. Para converter o valor, defina o <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade para um valor de tipo de exibição.  
  
> [!NOTE]
>  Se uma cadeia de caracteres de formato estiver em vigor para a célula, ela substituirá sua alteração do <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> a menos que você defina o valor de propriedade de <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> propriedade `true`.  
  
 O <xref:System.Windows.Forms.DataGridView.CellFormatting> evento também é útil quando você deseja definir <xref:System.Windows.Forms.DataGridViewCellStyle> propriedades para células individuais com base em seus valores. Para obter mais informações, confira [Como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Se a análise padrão de valores especificados pelo usuário não atender às suas necessidades, você pode lidar com o <xref:System.Windows.Forms.DataGridView.CellParsing> eventos do <xref:System.Windows.Forms.DataGridView> controle para fornecer uma análise personalizada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como: Formatar dados no Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
