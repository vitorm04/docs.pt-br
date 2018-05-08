---
title: Como usar um objeto ThicknessConverter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 119c4397dee76429e776378ee89fa49747dbfce4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Como usar um objeto ThicknessConverter
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar uma instância de <xref:System.Windows.ThicknessConverter> e usá-lo para alterar a espessura da borda de um.  
  
 O exemplo define um método personalizado chamado `changeThickness`; este método primeiro converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em uma separada [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância de <xref:System.Windows.Thickness>e posteriormente converte o conteúdo em um <xref:System.String>. Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.ThicknessConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.ListBoxItem> para uma instância de <xref:System.Windows.Thickness>. Esse valor é passado, em seguida, como o valor da <xref:System.Windows.Controls.Border.BorderThickness%2A> propriedade o <xref:System.Windows.Controls.Border>.  
  
 Este exemplo não é executado.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [Como: alterar a propriedade Margin](http://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [Como: converter um ListBoxItem em um novo tipo de dados](http://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
