---
title: Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)
Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> para desenhar círculos ou elipses em um formulário ou contêiner, no tempo de design e em tempo de execução. Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> para desenhar quadrados, retângulos ou retângulos com cantos arredondados em um formulário ou contêiner. Você também pode usar esse controle para desenhar formas em tempo de design e em tempo de execução.  
  
 Você pode personalizar a aparência de uma forma alterando a largura, a cor e o estilo de borda. O plano de fundo de uma forma é transparente por padrão. Você pode personalizar o plano de fundo para exibir uma cor sólida, um padrão, um preenchimento gradual (transição de uma cor para outra) ou uma imagem.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Para desenhar uma forma simples em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controlar do **Visual Basic PowerPacks** guia (para instalar, consulte [controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) no **caixa de ferramentas** para um controle de formulário ou contêiner.  
  
2.  Arraste o dimensionamento e mova as alças para dimensionar e posicionar a forma.  
  
     Você também pode dimensionar e posicionar a forma alterando o `Size` e `Position` propriedades o **propriedades** janela.  
  
     Para criar um retângulo com cantos arredondados, selecione o `CornerRadius` propriedade o **propriedades** janela e defina-o como um valor maior que 0.  
  
3.  No **propriedades** janela, opcionalmente, conjunto de propriedades adicionais para alterar a aparência da forma.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Para desenhar uma forma simples em tempo de execução  
  
1.  No menu **Projeto**, clique em **Adicionar Referência**.  
  
2.  No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.  
  
3.  No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Adicione o seguinte código em um procedimento do `Event`:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Personalizando Formas  
 Ao usar as configurações padrão, os controles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> são exibidos com uma borda preta sólida que é um pixel mais amplo e um plano de fundo transparente. Você pode alterar a largura, o estilo e a cor da borda definindo as propriedades. As propriedades adicionais permitem que você altere o plano de fundo de uma forma para uma cor sólida, um padrão, um preenchimento gradual ou uma imagem.  
  
 Antes de alterar o plano de fundo de uma forma, você deve saber como diversas propriedades interagem.  
  
-   A configuração de propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> não tem efeito, a menos que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> esteja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> substitui o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como um valor padrão, como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, o padrão será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. O plano de fundo será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, desde que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> seja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Para exibir um preenchimento gradual, a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> deve estar configurada como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> e a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> deve ser configurada com um valor diferente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Configurando a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> para uma imagem substitui todas as outras configurações de plano de fundo.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Para desenhar um círculo com uma borda personalizada  
  
1.  Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.  
  
3.  Defina a propriedade `BorderColor` com a cor desejada.  
  
4.  Defina a propriedade `BorderStyle` como qualquer valor diferente de `Solid`.  
  
5.  Defina o `BorderWidth` para o tamanho desejado, em pixels.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Para desenhar um círculo que tenha um preenchimento sólido  
  
1.  Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.  
  
3.  Defina a propriedade `BackColor` com a cor desejada.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Para desenhar um círculo que tenha um preenchimento padronizado  
  
1.  Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.  
  
3.  Defina a propriedade `BackColor` com a cor desejada para o plano de fundo.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
5.  Defina a propriedade `FillColor` com a cor desejada para o padrão.  
  
6.  Defina a propriedade `FillStyle` como qualquer valor diferente de `Transparent` ou `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Para desenhar um círculo que tenha um preenchimento gradual  
  
1.  Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.  
  
3.  Defina a propriedade `FillColor` com a cor desejada para a cor inicial.  
  
4.  Defina a propriedade `FillGradientColor` com a cor desejada para a cor final.  
  
5.  Defina a propriedade `FillGradientStyle` como um valor diferente de `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Para desenhar um círculo preenchido com uma imagem  
  
1.  Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.  
  
3.  Selecione o `BackgroundImage` propriedade e clique no **reticências** botão (…).  
  
4.  No **selecionar recurso** caixa de diálogo, selecione uma imagem a ser exibida. Se nenhum recurso de imagem estiver listado, clique em **importação** para navegar até o local de uma imagem.  
  
5.  Clique em **Okey** para inserir a imagem.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Como desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
