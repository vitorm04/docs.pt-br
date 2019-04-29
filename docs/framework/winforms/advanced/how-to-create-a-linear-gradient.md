---
title: 'Como: criar um gradiente linear'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: b836659821b54698b675d48acd4e46466001d654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937875"
---
# <a name="how-to-create-a-linear-gradient"></a>Como: criar um gradiente linear
GDI+ fornece gradientes lineares horizontais, verticais e diagonais. Por padrão, a cor em um gradiente linear muda uniformemente. No entanto, você pode personalizar um gradiente linear para que a cor mude de maneira não uniforme.  

> [!NOTE]
> Os exemplos neste artigo são métodos que são chamados de um controle <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  

O exemplo a seguir preenche uma linha, uma elipse e um retângulo com um pincel de gradiente linear horizontal.  
  
O <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> construtor recebe quatro argumentos: dois pontos e duas cores. O primeiro ponto (0, 10) é associado à primeira cor (vermelho) e o segundo ponto (200, 10) é associado à segunda cor (azul). Como seria de esperar, a linha desenhada de (10, 0) a (200, 10) muda gradualmente de vermelho para azul.  
  
 Os 10s nos pontos de (0, 10) e (200, 10) não são importantes. O que é importante é que os dois pontos têm a mesma segunda coordenada: a linha que os conecta é horizontal. A elipse e o retângulo também mudam gradualmente de vermelho para azul conforme a coordenada horizontal vai de 0 a 200.  
  
 A ilustração a seguir mostra a linha, a elipse e o retângulo. Observe que o gradiente de cores repete-se à medida que a coordenada horizontal aumenta além de 200.  
  
 ![Gradiente linear](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Para usar gradientes lineares horizontais  
  
- Passe o vermelho opaco e o azul opaco como o terceiro e o quarto argumentos, respectivamente.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 No exemplo anterior, os componentes de cor mudam linearmente conforme você vai de uma coordenada horizontal de 0 para uma coordenada horizontal de 200. Por exemplo, um ponto cuja primeira coordenada esteja a meio caminho entre 0 e 200 terá um componente azul a meio caminho entre 0 e 255.  
  
 GDI+ permite que você ajustar a maneira como a cor varia de uma borda de um gradiente para outra. Suponha que você queira criar um pincel de gradiente que mude de preto para vermelho de acordo com a tabela a seguir.  
  
|Coordenada horizontal|Componentes RGB|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Observe que o componente vermelho está na metade da intensidade quando a coordenada horizontal está a apenas 20% do caminho de 0 a 200.  
  
 O exemplo a seguir define o <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> propriedade para associar três intensidades relativas com três posições relativas. Como na tabela anterior, uma intensidade relativa de 0,5 é associada a uma posição relativa de 0,2. O código preenche uma elipse e um retângulo com o pincel de gradiente.  
  
 A ilustração a seguir mostra o retângulo e elipse resultantes.  
  
 ![Gradiente linear](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>Para personalizar os gradientes lineares  
  
- Passe o preto opaco e o vermelho opaco como o terceiro e o quarto argumentos, respectivamente.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Os gradientes nos exemplos anteriores eram horizontais; ou seja, a cor muda gradualmente à medida que você se move ao longo de qualquer linha horizontal. Você também pode definir gradientes verticais e gradientes diagonais.  
  
 O exemplo a seguir passa os pontos (0, 0) e (200, 100) para um <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> construtor. A cor azul é associada a (0, 0) e a cor verde é associada a (200, 100). Uma linha (com largura da caneta de 10) e uma elipse são preenchidas com o pincel de gradiente linear.  
  
 A ilustração a seguir mostra a linha e a elipse. Observe que a cor na elipse muda gradualmente à medida que você se move ao longo de qualquer linha paralela à linha que passa por (0, 0) e (200, 100).  
  
 ![Gradiente linear](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Para criar gradientes lineares diagonais  
  
- Passe o azul opaco e o verde opaco como o terceiro e o quarto argumentos, respectivamente.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Consulte também

- [Usando um Pincel de Gradiente para Preencher Formas](using-a-gradient-brush-to-fill-shapes.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
