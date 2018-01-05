---
title: Como desenhar uma linha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d667e8654f72226dc609a14aec650effe2d5c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line"></a>Como desenhar uma linha
Este exemplo mostra como desenhar linhas usando o <xref:System.Windows.Shapes.Line> elemento.  
  
 Para desenhar uma linha, crie um <xref:System.Windows.Shapes.Line> elemento. Use seu <xref:System.Windows.Shapes.Line.X1%2A> e <xref:System.Windows.Shapes.Line.Y1%2A> propriedades para definir seu ponto inicial; e use seu <xref:System.Windows.Shapes.Line.X2%2A> e <xref:System.Windows.Shapes.Line.Y2%2A> propriedades para definir seu ponto de extremidade. Finalmente, defina seu <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> porque uma linha sem um traço é invisível.  
  
 Definindo o <xref:System.Windows.Shapes.Shape.Fill%2A> elemento para uma linha não tem nenhum efeito, porque uma linha não possui interior.  
  
 O exemplo a seguir desenha três linhas dentro de um <xref:System.Windows.Controls.Canvas> elemento.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Shapes.Line>  
 [Exemplo de elementos de forma](http://go.microsoft.com/fwlink/?LinkID=160037)
