---
title: Como criar um gradiente de demarcador
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182639"
---
# <a name="how-to-create-a-path-gradient"></a>Como criar um gradiente de demarcador
A <xref:System.Drawing.Drawing2D.PathGradientBrush> classe permite que você personalize a maneira como você preenche uma forma com cores que mudam gradualmente. Por exemplo, você pode especificar uma cor para o centro de um caminho e outra cor para o limite de um caminho. Você também pode especificar cores separadas para cada um dos vários pontos ao longo do limite de um caminho.  
  
> [!NOTE]
> Em GDI+, um caminho é uma seqüência <xref:System.Drawing.Drawing2D.GraphicsPath> de linhas e curvas mantidas por um objeto. Para obter mais informações sobre os caminhos GDI+, consulte [Caminhos gráficos no GDI+](graphics-paths-in-gdi.md) e [Construção e Desenho de Caminhos](constructing-and-drawing-paths.md).  

Os exemplos neste artigo são métodos que são <xref:System.Windows.Forms.Control.Paint> chamados do manipulador de eventos de um controle.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Como preencher uma elipse com um gradiente de caminho  
  
- O exemplo a seguir preenche uma elipse com pincel de gradiente de caminho. A cor central é definida como azul e a cor do limite é definida como azul-piscina. A ilustração a seguir mostra a elipse preenchida.  
  
     ![Gradiente Path preenche uma elipse.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Por padrão, um pincel de gradiente de caminho não é estendido para fora do limite do caminho. Se você usar o pincel de gradiente de caminho para preencher uma figura que se estende para além do limite do caminho, a área da tela fora do caminho não será preenchida.  
  
     A ilustração a seguir mostra <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> o que acontece `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`se você alterar a chamada no seguinte código para :  
  
     ![O Caminho de Gradiente estendeu-se além do limite do caminho.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     O exemplo de código anterior foi projetado para <xref:System.Windows.Forms.PaintEventArgs> ser usado com formulários <xref:System.Windows.Forms.PaintEventHandler>do Windows, e requer o e, que é um parâmetro de .  
  
### <a name="to-specify-points-on-the-boundary"></a>Como especificar os pontos no limite  
  
- O exemplo a seguir constrói um pincel de gradiente de caminho de um caminho em forma de estrela. O código <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> define a propriedade, que define a cor no centroide da estrela como vermelha. Em seguida, <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> o código define a propriedade `colors` para especificar várias `points` cores (armazenadas na matriz) nos pontos individuais da matriz. A instrução de código final preenche o caminho em forma de estrela com o pincel de gradiente de caminho.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- O exemplo a seguir desenha <xref:System.Drawing.Drawing2D.GraphicsPath> um gradiente de caminho sem um objeto no código. O <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> construtor em particular no exemplo recebe uma matriz <xref:System.Drawing.Drawing2D.GraphicsPath> de pontos, mas não requer um objeto. Além disso, <xref:System.Drawing.Drawing2D.PathGradientBrush> note que o é usado para preencher um retângulo, não um caminho. O retângulo é maior do que o caminho fechado usado para definir o pincel, portanto, alguns dos retângulos não são pintados pelo pincel. A ilustração a seguir mostra o retângulo (linha pontilhada) e a parte do retângulo pintada pelo pincel gradiente do caminho:
  
     ![Porção de gradiente pintada pelo pincel de gradiente do caminho.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Como personalizar um gradiente de caminho  
  
- Uma maneira de personalizar um pincel de <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> gradiente de caminho é definir sua propriedade. O ajuste de escala do foco especifica um caminho interno que se encontra dentro do caminho principal. A cor central é exibida em qualquer lugar dentro desse caminho interno e não apenas no ponto central.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em uma trajetória elíptica. O código define a cor do limite como azul, define a cor do centro para azul-piscina e, em seguida, usa o pincel de gradiente de caminho para preencher o caminho elíptico.  
  
     Em seguida, o código define as escalas de foco do pincel de gradiente de caminho. A escala de foco de x é definida como 0,3 e a escala de foco de y é definida como 0,8. O código <xref:System.Drawing.Graphics.TranslateTransform%2A> chama o <xref:System.Drawing.Graphics> método de um objeto <xref:System.Drawing.Graphics.FillPath%2A> para que a chamada subseqüente preencha uma elipse que se senta à direita da primeira elipse.  
  
     Para ver o efeito de escalas de foco, imagine uma pequena elipse que compartilha seu centro com a elipse principal. A pequena elipse (interna) é a elipse principal dimensionada (sobre seu centro) horizontalmente por um fator de 0,3 e verticalmente por um fator de 0,8. Quando você vai do limite da elipse externa para o limite da elipse interna, a cor altera gradualmente de azul para azul-piscina. Quando você vai do limite da elipse interna ao centro compartilhado, a cor permanece azul-piscina.  
  
     A seguinte ilustração mostra a saída do código a seguir. A elipse à esquerda é azul-piscina somente no ponto central. A elipse à direita é azul-piscina em qualquer lugar dentro do caminho interno.  
  
 ![Efeito gradiente das escalas de foco](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Como personalizar com interpolação  
  
- Outra maneira de personalizar um pincel de gradiente de caminho é especificar uma matriz de cores de interpolação e uma matriz de posições de interpolação.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em um triângulo. O código <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> define a propriedade do pincel de gradiente de caminho para especificar uma matriz de cores de interpolação (verde escuro, aqua, azul) e uma matriz de posições de interpolação (0, 0,25, 1). Ao mudar do limite do triângulo ao ponto central, a cor gradualmente muda de verde-escuro para azul-piscina e, em seguida, de azul-piscina para azul. A alteração de verde-escuro para azul-piscina ocorre em 25 por cento da distância de verde-escuro para azul.  
  
     A ilustração a seguir mostra o triângulo preenchido com o pincel de gradiente de caminho personalizado.  
  
     ![Triângulo preenchido com pincel de gradiente de caminho personalizado.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Como definir o ponto central  
  
- Por padrão, o ponto central de um pincel de gradiente de caminho é o centroide de caminho usado para construir o pincel. Você pode alterar a localização do <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> ponto central <xref:System.Drawing.Drawing2D.PathGradientBrush> definindo a propriedade da classe.  
  
     O exemplo a seguir cria um pincel de gradiente de caminho com base em uma elipse. O centro da elipse é em (70, 35), mas o ponto central do pincel de gradiente de caminho é definido como (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     A ilustração a seguir mostra a elipse preenchida e o ponto central do pincel gradiente do caminho:  
  
     ![Caminho de gradiente com elipse e ponto central preenchidos.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Você pode definir o ponto central de um pincel de gradiente de caminho para um local fora do caminho que foi usado para construir o pincel. O exemplo a seguir substitui <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> a chamada para definir a propriedade no código anterior.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     A ilustração a seguir mostra a saída com esta alteração:  
  
     ![Caminho de gradiente com ponto central fora do caminho.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na ilustração anterior, os pontos na extremidade direita da elipse não são azul puro (embora muito parecido). As cores de gradiente são posicionadas como se o preenchimento tivesse atingido o ponto (145, 35) no qual a cor seria azul puro (0, 0, 255). Mas o preenchimento nunca atinge (145, 35), pois um pincel de gradiente de caminho pinta apenas dentro de seu caminho.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores são projetados para uso <xref:System.Windows.Forms.PaintEventArgs> `e`com formulários do <xref:System.Windows.Forms.Control.Paint> Windows e exigem , o que é um parâmetro do manipulador de eventos.  
  
## <a name="see-also"></a>Confira também

- [Usando um Pincel de Gradiente para Preencher Formas](using-a-gradient-brush-to-fill-shapes.md)
