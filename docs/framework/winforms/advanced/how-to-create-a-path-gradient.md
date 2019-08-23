---
title: 'Como: criar um gradiente de caminho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964410"
---
# <a name="how-to-create-a-path-gradient"></a>Como: criar um gradiente de caminho
A <xref:System.Drawing.Drawing2D.PathGradientBrush> classe permite que você personalize a maneira como preenche uma forma com cores que mudam gradualmente. Por exemplo, você pode especificar uma cor para o centro de um caminho e outra cor para o limite de um caminho. Você também pode especificar cores separadas para cada um dos vários pontos ao longo do limite de um caminho.  
  
> [!NOTE]
> No GDI+, um caminho é uma sequência de linhas e curvas mantidas por <xref:System.Drawing.Drawing2D.GraphicsPath> um objeto. Para obter mais informações sobre caminhos de GDI+, consulte [caminhos gráficos em GDI+](graphics-paths-in-gdi.md) e [construir e desenhar caminhos](constructing-and-drawing-paths.md).  

Os exemplos neste artigo são métodos que são chamados do manipulador de <xref:System.Windows.Forms.Control.Paint> eventos de um controle.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Como preencher uma elipse com um gradiente de caminho  
  
- O exemplo a seguir preenche uma elipse com pincel de gradiente de caminho. A cor central é definida como azul e a cor do limite é definida como azul-piscina. A ilustração a seguir mostra a elipse preenchida.  
  
     ![O caminho do gradiente preenche uma elipse.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Por padrão, um pincel de gradiente de caminho não é estendido para fora do limite do caminho. Se você usar o pincel de gradiente de caminho para preencher uma figura que se estende para além do limite do caminho, a área da tela fora do caminho não será preenchida.  
  
     A ilustração a seguir mostra o que acontece se você <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> alterar a chamada no código a `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`seguir para:  
  
     ![Caminho de gradiente estendido além do limite do caminho.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     O exemplo de código anterior foi projetado para uso com Windows Forms e requer o <xref:System.Windows.Forms.PaintEventArgs> e, que é um parâmetro de. <xref:System.Windows.Forms.PaintEventHandler>  
  
### <a name="to-specify-points-on-the-boundary"></a>Como especificar os pontos no limite  
  
- O exemplo a seguir constrói um pincel de gradiente de caminho de um caminho em forma de estrela. O código define a <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> Propriedade, que define a cor em centróides da estrela para vermelho. Em seguida, o código <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> define a propriedade para especificar várias cores (armazenadas `colors` na matriz) nos pontos individuais da `points` matriz. A instrução de código final preenche o caminho em forma de estrela com o pincel de gradiente de caminho.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- O exemplo a seguir desenha um gradiente de <xref:System.Drawing.Drawing2D.GraphicsPath> caminho sem um objeto no código. O construtor <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> específico no exemplo recebe uma matriz de pontos, mas não requer um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto. Além disso, observe que <xref:System.Drawing.Drawing2D.PathGradientBrush> o é usado para preencher um retângulo, não um caminho. O retângulo é maior do que o caminho fechado usado para definir o pincel, portanto, alguns dos retângulos não são pintados pelo pincel. A ilustração a seguir mostra o retângulo (linha pontilhada) e a parte do retângulo pintada pelo pincel de gradiente de caminho: 
  
     ![Parte de gradiente pintada pelo pincel de gradiente de caminho.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Como personalizar um gradiente de caminho  
  
- Uma maneira de personalizar um pincel de gradiente de caminho é <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> definir sua propriedade. O ajuste de escala do foco especifica um caminho interno que se encontra dentro do caminho principal. A cor central é exibida em qualquer lugar dentro desse caminho interno e não apenas no ponto central.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em uma trajetória elíptica. O código define a cor do limite como azul, define a cor do centro para azul-piscina e, em seguida, usa o pincel de gradiente de caminho para preencher o caminho elíptico.  
  
     Em seguida, o código define as escalas de foco do pincel de gradiente de caminho. A escala de foco de x é definida como 0,3 e a escala de foco de y é definida como 0,8. O código chama o <xref:System.Drawing.Graphics.TranslateTransform%2A> método de um <xref:System.Drawing.Graphics> objeto para <xref:System.Drawing.Graphics.FillPath%2A> que a chamada subsequente Preencha uma elipse que fica à direita da primeira elipse.  
  
     Para ver o efeito de escalas de foco, imagine uma pequena elipse que compartilha seu centro com a elipse principal. A pequena elipse (interna) é a elipse principal dimensionada (sobre seu centro) horizontalmente por um fator de 0,3 e verticalmente por um fator de 0,8. Quando você vai do limite da elipse externa para o limite da elipse interna, a cor altera gradualmente de azul para azul-piscina. Quando você vai do limite da elipse interna ao centro compartilhado, a cor permanece azul-piscina.  
  
     A seguinte ilustração mostra a saída do código a seguir. A elipse à esquerda é azul-piscina somente no ponto central. A elipse à direita é azul-piscina em qualquer lugar dentro do caminho interno.  
  
 ![Efeito de gradiente de escalas de foco](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Como personalizar com interpolação  
  
- Outra maneira de personalizar um pincel de gradiente de caminho é especificar uma matriz de cores de interpolação e uma matriz de posições de interpolação.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em um triângulo. O código define a <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> Propriedade do pincel de gradiente de caminho para especificar uma matriz de cores de interpolação (verde escuro, água, azul) e uma matriz de posições de interpolação (0, 0,25, 1). Ao mudar do limite do triângulo ao ponto central, a cor gradualmente muda de verde-escuro para azul-piscina e, em seguida, de azul-piscina para azul. A alteração de verde-escuro para azul-piscina ocorre em 25 por cento da distância de verde-escuro para azul.  
  
     A ilustração a seguir mostra o triângulo preenchido com o pincel de gradiente de caminho personalizado.  
  
     ![Triângulo preenchido com pincel de gradiente de caminho personalizado.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Como definir o ponto central  
  
- Por padrão, o ponto central de um pincel de gradiente de caminho é o centroide de caminho usado para construir o pincel. Você pode alterar o local do ponto central definindo a <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> propriedade <xref:System.Drawing.Drawing2D.PathGradientBrush> da classe.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em uma elipse. O centro da elipse é em (70, 35), mas o ponto central do pincel de gradiente de caminho é definido como (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     A ilustração a seguir mostra a elipse preenchida e o ponto central do pincel de gradiente do caminho:  
  
     ![Caminho de gradiente com elipse preenchida e ponto central.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Você pode definir o ponto central de um pincel de gradiente de caminho para um local fora do caminho que foi usado para construir o pincel. O exemplo a seguir substitui a chamada para definir <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> a propriedade no código anterior.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     A ilustração a seguir mostra a saída com essa alteração:  
  
     ![Caminho do gradiente com ponto central fora do caminho.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na ilustração anterior, os pontos na extremidade direita da elipse não são azul puro (embora muito parecido). As cores de gradiente são posicionadas como se o preenchimento tivesse atingido o ponto (145, 35) no qual a cor seria azul puro (0, 0, 255). Mas o preenchimento nunca atinge (145, 35), pois um pincel de gradiente de caminho pinta apenas dentro de seu caminho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores foram projetados para uso com Windows Forms, e eles exigem <xref:System.Windows.Forms.PaintEventArgs> `e`, que <xref:System.Windows.Forms.Control.Paint> é um parâmetro do manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Usando um Pincel de Gradiente para Preencher Formas](using-a-gradient-brush-to-fill-shapes.md)
