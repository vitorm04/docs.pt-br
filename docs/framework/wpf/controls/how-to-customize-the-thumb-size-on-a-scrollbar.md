---
title: Como personalizar o tamanho de elevador em um ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 689b73eb58cdfceb2ce5d4e76cbbc3d6c5af8967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Como personalizar o tamanho de elevador em um ScrollBar
Este tópico explica como definir a <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar> para um tamanho fixo e como especificar um tamanho mínimo para o <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho fixo. O exemplo define o <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> propriedade o <xref:System.Windows.Controls.Primitives.Thumb> para <xref:System.Double.NaN> e define a altura do <xref:System.Windows.Controls.Primitives.Thumb>.  Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura fixa, defina a largura do <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Código  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho mínimo. O exemplo define o valor de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura mínima, defina o <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Código  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Estilos e modelos ScrollBar](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
