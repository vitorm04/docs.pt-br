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
ms.openlocfilehash: 22215a155f4a204e3edeebc464413d5718290bb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577065"
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
- [Como: Alterar a propriedade Margin](https://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)
- [Como: Converter um ListBoxItem em um novo tipo de dados](https://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)
- [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
