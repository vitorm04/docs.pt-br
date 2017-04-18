---
title: 'Como: desenhar formas com os controles OvalShape e RectangleShape (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- OvalShape control
- shapes, drawing
- RectangleShape control
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7ed604db3fed8fcd8c8ec7f43e547442fc66bddb
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)
Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>controle para desenhar círculos ou elipses em um formulário ou contêiner, em tempo de design e tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>controle para desenhar quadrados, retângulos ou retângulos com cantos arredondados em um formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> Você também pode usar esse controle para desenhar formas em tempo de design e em tempo de execução.  
  
 Você pode personalizar a aparência de uma forma alterando a largura, a cor e o estilo de borda. O plano de fundo de uma forma é transparente por padrão. Você pode personalizar o plano de fundo para exibir uma cor sólida, um padrão, um preenchimento gradual (transição de uma cor para outra) ou uma imagem.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Para desenhar uma forma simples em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>de controle do **Visual Basic PowerPacks** guia (para instalar, consulte [controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) no **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
  
2.  Arraste o dimensionamento e mova as alças para dimensionar e posicionar a forma.  
  
     Você também pode redimensionar e posicionar a forma alterando o `Size` e `Position` propriedades no **propriedades** janela.  
  
     Para criar um retângulo com cantos arredondados, selecione o `CornerRadius` propriedade o **propriedades** janela e defini-lo como um valor maior que 0.  
  
3.  No **propriedades** janela, opcionalmente, conjunto de propriedades adicionais para alterar a aparência da forma.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Para desenhar uma forma simples em tempo de execução  
  
1.  Sobre o **projeto** menu, clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.  
  
3.  No **Editor de códigos**, adicione uma `Imports` ou `using` instrução na parte superior do módulo:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Adicione o seguinte código em um procedimento do `Event`:  
  
     [!code-cs[&#1; VbPowerpacksShape](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs) ] 
     [!code-vb [VbPowerpacksShape n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Personalizando Formas  
 Quando você usa as configurações padrão, o <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>controles são exibidos com uma borda preta sólida que é um pixel mais amplo e um plano de fundo transparente.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Você pode alterar a largura, o estilo e a cor da borda definindo as propriedades. As propriedades adicionais permitem que você altere o plano de fundo de uma forma para uma cor sólida, um padrão, um preenchimento gradual ou uma imagem.  
  
 Antes de alterar o plano de fundo de uma forma, você deve saber como diversas propriedades interagem.  
  
-   O <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>configuração de propriedade não terá efeito se a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A>propriedade é definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.</xref:Microsoft.VisualBasic.PowerPacks.BackStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>  
  
-   Se a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A>propriedade é definida, <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>as <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>substituições <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> </xref:Microsoft.VisualBasic.PowerPacks.FillStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A>  
  
-   Se a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A>propriedade é definida como um valor padrão como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, o padrão será exibido em <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> </xref:Microsoft.VisualBasic.PowerPacks.FillStyle> </xref:Microsoft.VisualBasic.PowerPacks.FillStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> O plano de fundo será exibido <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>contanto que a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A>propriedade é definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.</xref:Microsoft.VisualBasic.PowerPacks.BackStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>  
  
-   Para exibir um preenchimento de gradiente, a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A>propriedade deve ser definida e <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A>propriedade deve ser definida como um valor diferente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle>.</xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> </xref:Microsoft.VisualBasic.PowerPacks.FillStyle> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A>  
  
-   Definindo o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A>propriedade a uma imagem substitui todas as outras configurações de plano de fundo.</xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Para desenhar um círculo com uma borda personalizada  
  
1.  Arraste o `OvalShape` controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` , definida `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BorderColor` com a cor desejada.  
  
4.  Defina a propriedade `BorderStyle` como qualquer valor diferente de `Solid`.  
  
5.  Defina o `BorderWidth` para o tamanho desejado, em pixels.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Para desenhar um círculo que tenha um preenchimento sólido  
  
1.  Arraste o `OvalShape` controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` , definida `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BackColor` com a cor desejada.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Para desenhar um círculo que tenha um preenchimento padronizado  
  
1.  Arraste o `OvalShape` controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` , definida `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BackColor` com a cor desejada para o plano de fundo.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
5.  Defina a propriedade `FillColor` com a cor desejada para o padrão.  
  
6.  Defina a propriedade `FillStyle` como qualquer valor diferente de `Transparent` ou `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Para desenhar um círculo que tenha um preenchimento gradual  
  
1.  Arraste o `OvalShape` controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` , definida `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `FillColor` com a cor desejada para a cor inicial.  
  
4.  Defina a propriedade `FillGradientColor` com a cor desejada para a cor final.  
  
5.  Defina a propriedade `FillGradientStyle` como um valor diferente de `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Para desenhar um círculo preenchido com uma imagem  
  
1.  Arraste o `OvalShape` controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` , definida `Height` e `Width` como valores iguais.  
  
3.  Selecione o `BackgroundImage` propriedade e clique no **reticências** botão (...).  
  
4.  No **selecionar recurso** caixa de diálogo, selecione uma imagem a ser exibida. Se nenhum recurso de imagem estiver listado, clique em **importação** para navegar até o local de uma imagem.  
  
5.  Clique em **Okey** para inserir a imagem.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape></xref:Microsoft.VisualBasic.PowerPacks.OvalShape>   
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape></xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>   
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [Como desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
