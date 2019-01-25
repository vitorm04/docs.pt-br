---
title: 'Como: Usar a classe FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 7cb76ad4ffe4b4574a48212240b852e1f2253088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741893"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Como: Usar a classe FontSizeConverter
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar uma instância de <xref:System.Windows.FontSizeConverter> e usá-lo para alterar o tamanho da fonte.  
  
 O exemplo define um método personalizado chamado `changeSize` que converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância do <xref:System.Double>e posteriormente em um <xref:System.String>. Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.FontSizeConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de uma <xref:System.Windows.Controls.ListBoxItem> a uma instância do <xref:System.Double>. Esse valor, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriedade do <xref:System.Windows.Controls.TextBlock> elemento.  
  
 Este exemplo também define um segundo método personalizado que é chamado `changeFamily`. Este método converte o <xref:System.Windows.Controls.ContentControl.Content%2A> do <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.String>e, em seguida, passa o valor para o <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriedade do <xref:System.Windows.Controls.TextBlock> elemento.  
  
 Este exemplo não é executado.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FontSizeConverter>
