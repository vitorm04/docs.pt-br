---
title: Como unir linhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f02da181d66f7bb26a8414782e42eff2570e6918
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-join-lines"></a>Como unir linhas
Uma junção de linha é a área comum que é formada por duas linhas cujas extremidades se encontram ou se sobrepõem. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece três estilos de junção de linha: malhete, bisel e redonda. Estilo de junção de linha é uma propriedade do <xref:System.Drawing.Pen> classe. Quando você especifica um estilo de linha de junção para um <xref:System.Drawing.Pen> do objeto, que o estilo de junção será aplicado a todas as linhas conectadas em qualquer <xref:System.Drawing.Drawing2D.GraphicsPath> objeto desenhado usando essa caneta.  
  
 A ilustração a seguir mostra os resultados do exemplo de junção de linha biselada.  
  
 ![Canetas](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>Exemplo  
 Você pode especificar o estilo de junção de linha usando o <xref:System.Drawing.Pen.LineJoin%2A> propriedade o <xref:System.Drawing.Pen> classe. O exemplo demonstra uma junção de linha biselada entre uma linha horizontal e uma linha vertical. No código a seguir, o valor <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atribuído para o <xref:System.Drawing.Pen.LineJoin%2A> propriedade é um membro do <xref:System.Drawing.Drawing2D.LineJoin> enumeração. Os outros membros do <xref:System.Drawing.Drawing2D.LineJoin> enumeração são <xref:System.Drawing.Drawing2D.LineJoin.Miter> e <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
