---
title: Pincéis e formas preenchidas no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 197678cfdced1e17ad87f521a30c7103c49df4e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624159"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pincéis e formas preenchidas no GDI+
Uma forma fechada, como um retângulo ou uma elipse, é composta por uma estrutura de tópicos e um interior. A estrutura de tópicos é desenhada com uma caneta e o interior é preenchido com um pincel. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece várias classes de pincel para preencher os interiores das formas fechadas: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, e <xref:System.Drawing.Drawing2D.PathGradientBrush>. Todas essas classes herdam o <xref:System.Drawing.Brush> classe. A ilustração a seguir mostra um retângulo preenchido com um pincel sólido e uma elipse preenchida com um pincel de hachura.  
  
 ![Formas Preenchidas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Pincéis Sólidos  
 Para preencher uma forma fechada, você precisa de uma instância das <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Brush>. A instância das <xref:System.Drawing.Graphics> classe fornece métodos, tais como <xref:System.Drawing.Graphics.FillRectangle%2A> e <xref:System.Drawing.Graphics.FillEllipse%2A>e o <xref:System.Drawing.Brush> armazena atributos do preenchimento, como cor e padrão. O <xref:System.Drawing.Brush> é passado como um dos argumentos para o método de preenchimento. O exemplo de código a seguir mostra como preencher uma elipse com uma cor vermelha sólida.  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  No exemplo anterior, o pincel é do tipo <xref:System.Drawing.SolidBrush>, que herda de <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Pincéis de Hachura  
 Ao preencher uma forma com um pincel de hachura, é necessário especificar uma cor de primeiro plano, uma cor da tela de fundo e um estilo de hachura. A cor de primeiro plano é a cor da hachura.  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece mais de 50 estilos de hachura; os três estilos mostrados na ilustração a seguir são <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, e <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Formas Preenchidas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pincéis de Textura  
 Com um pincel de textura, é possível preencher uma forma com um padrão armazenado em um bitmap. Por exemplo, suponha que a imagem a seguir está armazenada em um arquivo de disco chamado `MyTexture.bmp`.  
  
 ![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 O exemplo de código a seguir mostra como preencher uma elipse repetindo a imagem armazenada em `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 A ilustração a seguir mostra a elipse preenchida.  
  
 ![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pincéis de Gradiente  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oferece dois tipos de pincéis de gradiente: linear e de caminho. É possível usar um pincel de gradiente linear para preencher uma forma com uma cor que muda gradualmente à medida que a forma é movida horizontal, vertical ou diagonalmente. O exemplo de código a seguir mostra como preencher uma elipse com um pincel de gradiente horizontal que muda de azul para verde ao mover da borda esquerda para a borda direita da elipse.  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 A ilustração a seguir mostra a elipse preenchida.  
  
 ![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Um pincel de gradiente de caminho pode ser configurado para alterar a cor ao mover do centro de uma forma para a borda.  
  
 ![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Pincéis de gradiente de caminho são bastante flexíveis. O pincel de gradiente usado para preencher o triângulo nas seguintes ilustrações altera gradualmente de vermelho no centro para cada uma das três cores diferentes nos vértices.  
  
 ![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Como: Desenhar um retângulo preenchido em um formulário do Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Como: Desenhar uma elipse preenchida em um formulário do Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
