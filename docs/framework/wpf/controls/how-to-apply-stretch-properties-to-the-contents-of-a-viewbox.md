---
title: 'Como: Aplicar propriedades Stretch ao conteúdo de uma caixa de exibição'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 08358ea07e0c41e3b7cdf52251a3ed4296035e2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209873"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Como: Aplicar propriedades Stretch ao conteúdo de uma caixa de exibição
## <a name="example"></a>Exemplo  
 Este exemplo mostra como alterar o valor de <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> e <xref:System.Windows.Controls.Viewbox.Stretch%2A> propriedades de um <xref:System.Windows.Controls.Viewbox>.  
  
 O primeiro exemplo usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.Viewbox> elemento. Ele atribui uma <xref:System.Windows.FrameworkElement.MaxWidth%2A> e <xref:System.Windows.FrameworkElement.MaxHeight%2A> de 400. O exemplo aninha um <xref:System.Windows.Controls.Image> elemento dentro do <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button> elementos que correspondem aos valores de propriedade para o <xref:System.Windows.Controls.Viewbox.Stretch%2A> e <xref:System.Windows.Controls.StretchDirection> enumerações manipulam o comportamento de alongamento de aninhada <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Os seguintes identificadores de arquivos de lógica de <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos que o anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo define.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Viewbox>
- <xref:System.Windows.Media.Stretch>
- <xref:System.Windows.Controls.StretchDirection>
