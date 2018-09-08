---
title: Como usar as propriedades anexas de tela para posicionar elementos filho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 89327b834dfd71c0a7420eb42a598b98cdb5e9d8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208485"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>Como usar as propriedades anexas de tela para posicionar elementos filho
Este exemplo mostra como usar as propriedades anexas de <xref:System.Windows.Controls.Canvas> para posicionar elementos filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona quatro <xref:System.Windows.Controls.Button> elementos como elementos filho de um pai <xref:System.Windows.Controls.Canvas>. Cada elemento é representado por um <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, e <xref:System.Windows.Controls.Canvas.Top%2A>.
Cada <xref:System.Windows.Controls.Button> é posicionado em relação ao pai <xref:System.Windows.Controls.Canvas> e de acordo com seu valor atribuído da propriedade.  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
