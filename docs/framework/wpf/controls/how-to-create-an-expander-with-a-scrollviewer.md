---
title: Como criar um expansor com um ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553056"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Como criar um expansor com um ScrollViewer
Este exemplo mostra como criar um <xref:System.Windows.Controls.Expander> controle que contém conteúdo complexo, como uma imagem e texto. O exemplo também inclui o conteúdo do <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Expander>. O exemplo usa um <xref:System.Windows.Controls.Primitives.BulletDecorator> controle, que contém uma imagem e texto, para definir o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. Um <xref:System.Windows.Controls.ScrollViewer> controle fornece um método para rolar o conteúdo expandido.  
  
 Observe que o exemplo define o <xref:System.Windows.FrameworkElement.Height%2A> propriedade o <xref:System.Windows.Controls.ScrollViewer> em vez de no conteúdo. Se o <xref:System.Windows.FrameworkElement.Height%2A> é definido no conteúdo, o <xref:System.Windows.Controls.ScrollViewer> não permite que o usuário role o conteúdo. O <xref:System.Windows.FrameworkElement.Width%2A> propriedade é definida no <xref:System.Windows.Controls.Expander> controle e essa configuração aplica-se ao <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o conteúdo expandido.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Expander>  
 [Visão geral de Expander](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
