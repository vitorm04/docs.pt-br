---
title: Formatação de dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: ae1947cf7c3825553837fa5f1ee288114988d28f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527768"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatação de dados no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle fornece conversão automática entre valores de célula e os tipos de dados que exibem as colunas pai. Colunas da caixa de texto, por exemplo, exibem representações de valores de data, hora, número e enumeração, e convertem valores de cadeia de caracteres inseridos pelo usuário nos tipos necessários para o armazenamento de dados.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatação com a classe DataGridViewCellStyle  
 O <xref:System.Windows.Forms.DataGridView> controle fornece a formatação de dados básicos de valores de célula por meio de <xref:System.Windows.Forms.DataGridViewCellStyle> classe. Você pode usar o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade para valores de data, hora, número e enumeração de formato para a cultura padrão atual usando especificadores de formato descritos na [tipos de formatação](../../../../docs/standard/base-types/formatting-types.md). Você também pode formatar esses valores específicos de cultura usando a <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> propriedade. O formato especificado é usado para exibir dados e analisar dados digitados pelo usuário no formato especificado.  
  
 O <xref:System.Windows.Forms.DataGridViewCellStyle> classe fornece propriedades de formatação adicionais para wordwrap, alinhamento de texto e a exibição personalizada de valores nulos de banco de dados. Para obter mais informações, consulte [Como formatar dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatação com o evento CellFormatting  
 Se a formatação básica não atender às suas necessidades, você pode fornecer dados personalizados de formatação em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento. O <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passado para o manipulador tem um <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade que inicialmente contém o valor da célula. Normalmente, esse valor é automaticamente convertido no tipo de exibição. Para converter o valor, defina o <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade para um valor do tipo de exibição.  
  
> [!NOTE]
>  Se uma cadeia de caracteres de formato está em vigor para a célula, ela substitui a alteração do <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> valor de propriedade, a menos que você defina o <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> propriedade `true`.  
  
 O <xref:System.Windows.Forms.DataGridView.CellFormatting> evento também é útil quando você deseja definir <xref:System.Windows.Forms.DataGridViewCellStyle> propriedades para células individuais com base em seus valores. Para obter mais informações, consulte [Como personalizar a formatação de dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Se a análise de padrão de valores especificados pelo usuário não atender às suas necessidades, você pode manipular o <xref:System.Windows.Forms.DataGridView.CellParsing> evento o <xref:System.Windows.Forms.DataGridView> controle para fornecer análise personalizado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Como formatar dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
