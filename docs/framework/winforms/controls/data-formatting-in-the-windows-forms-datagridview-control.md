---
title: Formatação de dados no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743990"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatação de dados no controle DataGridView dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> fornece conversão automática entre valores de célula e os tipos de dados que as colunas pai exibem. Colunas da caixa de texto, por exemplo, exibem representações de valores de data, hora, número e enumeração, e convertem valores de cadeia de caracteres inseridos pelo usuário nos tipos necessários para o armazenamento de dados.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatação com a classe DataGridViewCellStyle  
 O controle <xref:System.Windows.Forms.DataGridView> fornece formatação de dados básica de valores de célula por meio da classe <xref:System.Windows.Forms.DataGridViewCellStyle>. Você pode usar a propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> para formatar os valores de data, hora, número e enumeração para a cultura padrão atual usando os especificadores de formato descritos em [tipos de formatação](../../../standard/base-types/formatting-types.md). Você também pode formatar esses valores para culturas específicas usando a propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>. O formato especificado é usado para exibir dados e analisar dados digitados pelo usuário no formato especificado.  
  
 A classe <xref:System.Windows.Forms.DataGridViewCellStyle> fornece propriedades de formatação adicionais para WordWrap, alinhamento de texto e a exibição personalizada de valores de banco de dados nulos. Para obter mais informações, consulte [Como formatar dados no controle DataGridView do Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatação com o evento CellFormatting  
 Se a formatação básica não atender às suas necessidades, você poderá fornecer formatação de dados personalizada em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. O <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passado para o manipulador tem uma propriedade <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> que inicialmente contém o valor da célula. Normalmente, esse valor é automaticamente convertido no tipo de exibição. Para converter o valor por conta própria, defina a propriedade <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> como um valor do tipo de exibição.  
  
> [!NOTE]
> Se uma cadeia de caracteres de formato estiver em vigor para a célula, ela substituirá a alteração do valor da propriedade <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, a menos que você defina a propriedade <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> como `true`.  
  
 O evento <xref:System.Windows.Forms.DataGridView.CellFormatting> também é útil quando você deseja definir <xref:System.Windows.Forms.DataGridViewCellStyle> Propriedades para células individuais com base em seus valores. Para obter mais informações, consulte [Como personalizar a formatação de dados no controle DataGridView do Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Se a análise padrão de valores especificados pelo usuário não atender às suas necessidades, você poderá manipular o evento <xref:System.Windows.Forms.DataGridView.CellParsing> do controle de <xref:System.Windows.Forms.DataGridView> para fornecer análise personalizada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como formatar dados no controle DataGridView do Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Como personalizar a formatação de dados no controle DataGridView do Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
