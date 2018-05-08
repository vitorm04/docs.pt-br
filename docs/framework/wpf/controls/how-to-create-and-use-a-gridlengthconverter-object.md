---
title: Como criar e usar um objeto GridLengthConverter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 7c31b9e6599557783097c73468305dacfb19fc4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Como criar e usar um objeto GridLengthConverter
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar e usar uma instância de <xref:System.Windows.GridLengthConverter>. O exemplo define um método personalizado chamado `changeCol`, que passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.GridLengthConverter> que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.ListBoxItem> para uma instância de <xref:System.Windows.GridLength>. O valor convertido, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.ColumnDefinition.Width%2A> propriedade o <xref:System.Windows.Controls.ColumnDefinition> elemento.  
  
 O exemplo também define um segundo método personalizado, chamado `changeColVal`. Este método converte o <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> de um <xref:System.Windows.Controls.Slider> para um <xref:System.String> e, em seguida, passa que o valor de volta para o <xref:System.Windows.Controls.ColumnDefinition> como o <xref:System.Windows.Controls.ColumnDefinition.Width%2A> do elemento.  
  
 Observe que um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo define o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
