---
title: 'Como: Usar um objeto ThicknessConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 653137c0707c2b7ee51f6bdac6bb2501f1845e1a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747337"
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Como: Usar um objeto ThicknessConverter
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar uma instância de <xref:System.Windows.ThicknessConverter> e usá-lo para alterar a espessura de uma borda.  
  
 O exemplo define um método personalizado chamado `changeThickness`; esse método primeiro converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância do <xref:System.Windows.Thickness>e posteriormente converte o conteúdo em um <xref:System.String>. Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.ThicknessConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de uma <xref:System.Windows.Controls.ListBoxItem> a uma instância do <xref:System.Windows.Thickness>. Esse valor, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.Border.BorderThickness%2A> propriedade do <xref:System.Windows.Controls.Border>.  
  
 Este exemplo não é executado.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- [Como: Alterar a propriedade Margin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))
- [Como: Converter um ListBoxItem em um novo tipo de dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))
- [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
