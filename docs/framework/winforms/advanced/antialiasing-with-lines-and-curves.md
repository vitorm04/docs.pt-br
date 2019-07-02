---
title: Suavização com linhas e curvas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 871c5cb3cd9356f677633acb04fe82021a9787c5
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506144"
---
# <a name="antialiasing-with-lines-and-curves"></a>Suavização com linhas e curvas
Quando você usa o GDI+ para desenhar uma linha, você fornece o ponto de partida e final da linha, mas não é necessário fornecer todas as informações sobre os pixels individuais na linha. GDI+ funciona em conjunto com o software de driver de vídeo para determinar quais pixels serão ativados para mostrar a linha em um dispositivo de vídeo específico.  
  
## <a name="aliasing"></a>Serrilhado  
 Considere a linha reta vermelha que vai do ponto (4, 2) até o ponto (16, 10). Suponha que o sistema de coordenadas tem sua origem no canto superior esquerdo e que a unidade de medida é o pixel. Suponha também que o eixo X aponta para a direita e o eixo Y aponta para baixo. A ilustração a seguir mostra uma exibição ampliada da linha vermelha desenhada em uma tela de fundo multicolorida.  
  
 ![Linha, sem suavização](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Os pixels vermelhos usados para renderizar a linha são opacos. Não existem pixels parcialmente transparentes na linha. Esse tipo de processamento de linha dá a esta uma aparência denteada, fazendo com que se pareça com uma escada. Essa técnica de representar uma linha com uma escada é chamada de serrilhado; a escada é um alias para a linha teórica.  
  
## <a name="antialiasing"></a>Suavização  
 Uma técnica mais sofisticada para renderizar uma linha envolve o uso de pixels parcialmente transparentes junto com pixels opacos. Pixels são definidas como vermelho puro ou como uma mistura de vermelho e a cor da tela de fundo, dependendo da sua proximidade da linha. Esse tipo de renderização é chamado de suavização e resulta em uma linha que o olho humano percebe como mais suave. A ilustração a seguir mostra como determinados pixels são mesclados com a tela de fundo para produzir uma linha suavizada.  
  
 ![Suavizando uma linha](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 A suavização, também chamada de antialiasing, também pode ser aplicada a curvas. A ilustração a seguir mostra uma exibição ampliada de uma elipse suavizada.  
  
 ![Suavização de curvas](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 A ilustração a seguir mostra a mesma elipse em seu tamanho real, uma vez sem suavização e outra com suavização.  
  
 ![Exemplo de suavização](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Para desenhar linhas e curvas que usam suavização, crie uma instância das <xref:System.Drawing.Graphics> de classe e defina sua <xref:System.Drawing.Graphics.SmoothingMode%2A> propriedade a ser <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ou <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Em seguida, chame um dos métodos de desenho desse mesmo <xref:System.Drawing.Graphics> classe.  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Como: Usar suavização com texto](how-to-use-antialiasing-with-text.md)
