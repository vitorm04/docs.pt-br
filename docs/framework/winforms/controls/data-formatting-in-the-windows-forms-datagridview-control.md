---
title: Formatação de dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969180"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatação de dados no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle fornece conversão automática entre valores de célula e os tipos de dados que as colunas pai exibem. Colunas da caixa de texto, por exemplo, exibem representações de valores de data, hora, número e enumeração, e convertem valores de cadeia de caracteres inseridos pelo usuário nos tipos necessários para o armazenamento de dados.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatação com a classe DataGridViewCellStyle  
 O <xref:System.Windows.Forms.DataGridView> controle fornece a formatação de dados básica de valores de <xref:System.Windows.Forms.DataGridViewCellStyle> célula por meio da classe. Você pode usar a <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade para formatar os valores de data, hora, número e enumeração para a cultura padrão atual usando os especificadores de formato descritos em [tipos de formatação](../../../standard/base-types/formatting-types.md). Você também pode formatar esses valores para culturas específicas usando a <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> propriedade. O formato especificado é usado para exibir dados e analisar dados digitados pelo usuário no formato especificado.  
  
 A <xref:System.Windows.Forms.DataGridViewCellStyle> classe fornece propriedades de formatação adicionais para WordWrap, alinhamento de texto e a exibição personalizada de valores de banco de dados nulos. Para obter mais informações, confira [Como: Formate dados no controle](how-to-format-data-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatação com o evento CellFormatting  
 Se a formatação básica não atender às suas necessidades, você poderá fornecer formatação de dados personalizada em um manipulador para <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> o evento. O <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passado para o manipulador tem uma <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade que inicialmente contém o valor da célula. Normalmente, esse valor é automaticamente convertido no tipo de exibição. Para converter o valor por conta própria, <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> defina a propriedade como um valor do tipo de exibição.  
  
> [!NOTE]
> Se uma cadeia de caracteres de formato estiver em vigor para a célula, ela substituirá <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> a alteração do valor da propriedade <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> , a `true`menos que você defina a propriedade como.  
  
 O <xref:System.Windows.Forms.DataGridView.CellFormatting> evento também é útil quando você deseja definir <xref:System.Windows.Forms.DataGridViewCellStyle> Propriedades para células individuais com base em seus valores. Para obter mais informações, confira [Como: Personalizar a formatação de dados no controle](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.  
  
 Se a análise padrão de valores especificados pelo usuário não atender às suas necessidades, você poderá manipular o <xref:System.Windows.Forms.DataGridView.CellParsing> evento <xref:System.Windows.Forms.DataGridView> do controle para fornecer análise personalizada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como: Formatar dados no controle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Como: Personalizar a formatação de dados no controle Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
