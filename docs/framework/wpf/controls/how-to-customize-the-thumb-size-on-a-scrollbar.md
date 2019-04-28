---
title: 'Como: Personalizar o tamanho do elevador em um ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911047"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Como: Personalizar o tamanho do elevador em um ScrollBar
Este tópico explica como definir as <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar> para um tamanho fixo e como especificar um tamanho mínimo para o <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho fixo. O exemplo define o <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> propriedade do <xref:System.Windows.Controls.Primitives.Thumb> à <xref:System.Double.NaN> e define a altura do <xref:System.Windows.Controls.Primitives.Thumb>.  Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura fixa, defina a largura do <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Código  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho mínimo. O exemplo define o valor de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura mínima, defina o <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Código  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Consulte também

- [Estilos e modelos ScrollBar](scrollbar-styles-and-templates.md)
