---
title: Tipos de sistemas de coordenadas
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
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a>Tipos de sistemas de coordenadas
O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] usa três espaços de coordenadas: mundo, página e dispositivo. Coordenadas de mundo são as coordenadas usadas para modelar um mundo gráfico específico e são as coordenadas que você passa para métodos no .NET Framework. Coordenadas de página fazem referência ao sistema de coordenadas usado por uma superfície de desenho, como um formulário ou controle. Coordenadas de dispositivo são as coordenadas usadas pelo dispositivo físico em que o desenho está sendo feito, como uma tela ou uma folha de papel. Quando você fizer a chamada `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, os pontos que você passa para o <xref:System.Drawing.Graphics.DrawLine%2A> método —`(0, 0)` e `(160, 80)`— no espaço de coordenadas do mundo. Antes que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] possa desenhar a linha na tela, as coordenadas passam por uma sequência de transformações. Uma transformação, chamada transformação global, converte coordenadas de mundo em coordenadas de página e outra transformação, chamada transformação de página, converte coordenadas de página em coordenadas de dispositivo.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformações e sistemas de coordenadas  
 Suponha que você queira trabalhar com um sistema de coordenadas cuja origem está no corpo da área de cliente em vez do canto superior esquerdo. Digamos, por exemplo, que você queira que a origem esteja a 100 pixels da borda esquerda da área de cliente e a 50 pixels da parte superior da área de cliente. A ilustração a seguir mostra esse sistema de coordenadas.  
  
 ![Sistema de coordenadas](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Quando faz a chamada `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, você obtém a linha mostrada na ilustração a seguir.  
  
 ![Sistema de coordenadas](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 As coordenadas dos pontos de extremidade da sua linha nos três espaços de coordenadas são as seguintes:  
  
|||  
|-|-|  
|Mundo|(0, 0) a (160, 80)|  
|Página|(100, 50) a (260, 130)|  
|Dispositivo|(100, 50) a (260, 130)|  
  
 Observe que o espaço de coordenadas de página tem sua origem no canto superior esquerdo da área de cliente; sempre será esse o caso. Observe também que, como a unidade de medida é o pixel, as coordenadas do dispositivo são as mesmas que as coordenadas da página. Se você definir a unidade de medida como algo diferente de pixels (por exemplo, polegadas), as coordenadas do dispositivo serão diferentes das coordenadas da página.  
  
 A transformação do mundo, que mapeia as coordenadas do mundo em coordenadas da página, é mantida no <xref:System.Drawing.Graphics.Transform%2A> propriedade o <xref:System.Drawing.Graphics> classe. No exemplo anterior, a transformação global é uma translação de 100 unidades na direção x e 50 unidades na direção y. O exemplo a seguir define a transformação global de um <xref:System.Drawing.Graphics> de objeto e, em seguida, usa <xref:System.Drawing.Graphics> objeto para desenhar a linha mostrada na figura anterior:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 A transformação de página mapeia as coordenadas da página para coordenadas do dispositivo. O <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.PageUnit%2A> e <xref:System.Drawing.Graphics.PageScale%2A> propriedades para manipular a transformação de página. O <xref:System.Drawing.Graphics> classe também fornece duas propriedades somente leitura, <xref:System.Drawing.Graphics.DpiX%2A> e <xref:System.Drawing.Graphics.DpiY%2A>, para examinar horizontais e verticais pontos por polegada de dispositivo de vídeo.  
  
 Você pode usar o <xref:System.Drawing.Graphics.PageUnit%2A> propriedade o <xref:System.Drawing.Graphics> classe para especificar uma unidade de medida diferente de pixel.  
  
> [!NOTE]
>  Não é possível definir o <xref:System.Drawing.Graphics.PageUnit%2A> propriedade <xref:System.Drawing.GraphicsUnit.World>, como essa não é uma unidade física e fará com que uma exceção.  
  
 O exemplo a seguir desenha uma linha de (0, 0) para (2, 1), no qual o ponto (2, 1) está 2 polegadas à direita e 1 polegada abaixo do ponto (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Se você não especificar uma largura de caneta ao construir a caneta, o exemplo anterior desenhará uma linha com uma polegada de largura. Você pode especificar a largura da caneta no segundo argumento para o <xref:System.Drawing.Pen> construtor:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Se supusermos que o dispositivo de vídeo tem 96 pontos por polegada na direção horizontal e 96 pontos por polegada na direção vertical, os pontos de extremidade da linha no exemplo anterior terão as seguintes coordenadas nos três espaços de coordenadas:  
  
|||  
|-|-|  
|Mundo|(0, 0) a (2, 1)|  
|Página|(0, 0) a (2, 1)|  
|Dispositivo|(0, 0) a (192, 96)|  
  
 Observe que, como a origem do espaço de coordenadas de mundo está no canto superior esquerdo da área de cliente, as coordenadas de página serão as mesmas que as coordenadas de mundo.  
  
 É possível combinar as transformações global e de página para obter uma variedade de resultados. Por exemplo, suponha que você queira usar polegadas como a unidade de medida e queira que a origem se seu sistema de coordenadas esteja a 2 polegadas da borda esquerda da área de cliente e a 1/2 polegada da parte superior da área de cliente. O exemplo a seguir define as transformações de mundo e página de um <xref:System.Drawing.Graphics> de objeto e, em seguida, desenha uma linha de (0, 0) para (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 A ilustração a seguir mostra a linha e o sistema de coordenadas.  
  
 ![Sistema de coordenadas](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Se supusermos que o dispositivo de vídeo tem 96 pontos por polegada na direção horizontal e 96 pontos por polegada na direção vertical, os pontos de extremidade da linha no exemplo anterior terão as seguintes coordenadas nos três espaços de coordenadas:  
  
|||  
|-|-|  
|Mundo|(0, 0) a (2, 1)|  
|Página|(2, 0.5) a (4, 1.5)|  
|Dispositivo|(192, 48) a (384, 144)|  
  
## <a name="see-also"></a>Consulte também  
 [Sistemas de Coordenadas e Transformações](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Representação Matricial de Transformações](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
