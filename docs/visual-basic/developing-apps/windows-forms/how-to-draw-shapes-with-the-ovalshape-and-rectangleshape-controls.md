---
title: "Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Controle OvalShape"
  - "Controle RectangleShape"
  - "formas, desenho"
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> para desenhar círculos ou elipses em um formulário ou contêiner, no tempo de design e em tempo de execução.  Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> para desenhar quadrados, retângulos ou retângulos com cantos arredondados em um formulário ou contêiner.  Você também pode usar esse controle para desenhar formas em tempo de design e em tempo de execução.  
  
 Você pode personalizar a aparência de uma forma alterando a largura, a cor e o estilo de borda.  O plano de fundo de uma forma é transparente por padrão. Você pode personalizar o plano de fundo para exibir uma cor sólida, um padrão, um preenchimento gradual \(transição de uma cor para outra\) ou uma imagem.  
  
### Para desenhar uma forma simples em tempo de design  
  
1.  Arraste o controle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> da guia **Visual Basic PowerPacks** \(para instalar, consulte [Controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)\) na **Caixa de Ferramentas** para um formulário ou controle de contêiner.  
  
2.  Arraste o dimensionamento e mova as alças para dimensionar e posicionar a forma.  
  
     Você também pode dimensionar e posicionar a forma alterando as propriedades `Size` e `Position` na janela **Propriedades**.  
  
     Para criar um retângulo com cantos arredondados, selecione a propriedade `CornerRadius` na janela **Propriedades** e defini\-a para um valor maior que 0.  
  
3.  Na janela **Propriedades**, opcionalmente defina propriedades adicionais para alterar a aparência da forma.  
  
### Para desenhar uma forma simples em tempo de execução  
  
1.  No menu **Projeto**, clique em **Adicionar Referência**.  
  
2.  Na caixa de diálogo **Adicionar Referência**, selecione **Microsoft.VisualBasic.PowerPacks.VS** e, em seguida, clique em **OK**.  
  
3.  No **Editor de Código**, adicione uma instrução `Imports` ou `using` na parte superior do módulo:  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  Adicione o seguinte código em um procedimento do `Event`:  
  
     [!code-cs[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## Personalizando Formas  
 Ao usar as configurações padrão, os controles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> são exibidos com uma borda preta sólida que é um pixel mais amplo e um plano de fundo transparente.  Você pode alterar a largura, o estilo e a cor da borda definindo as propriedades.  As propriedades adicionais permitem que você altere o plano de fundo de uma forma para uma cor sólida, um padrão, um preenchimento gradual ou uma imagem.  
  
 Antes de alterar o plano de fundo de uma forma, você deve saber como diversas propriedades interagem.  
  
-   A configuração de propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> não tem efeito, a menos que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> esteja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.  
  
-   Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> substitui o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como um valor padrão, como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, o padrão será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.  O plano de fundo será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, desde que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> seja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.  
  
-   Para exibir um preenchimento gradual, a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> deve estar configurada como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> e a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> deve ser configurada com um valor diferente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle>.  
  
-   Configurando a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> para uma imagem substitui todas as outras configurações de plano de fundo.  
  
#### Para desenhar um círculo com uma borda personalizada  
  
1.  Arraste o controle `OvalShape` da guia **Visual Basic PowerPacks** na **Caixa de Ferramentas** para um controle de contêiner ou formulário.  
  
2.  Na janela **Propriedades**, na propriedade `Size`, defina `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BorderColor` com a cor desejada.  
  
4.  Defina a propriedade `BorderStyle` como qualquer valor diferente de `Solid`.  
  
5.  Defina o `BorderWidth` para o tamanho desejado, em pixels.  
  
#### Para desenhar um círculo que tenha um preenchimento sólido  
  
1.  Arraste o controle `OvalShape` da guia **Visual Basic PowerPacks** na **Caixa de Ferramentas** para um controle de contêiner ou formulário.  
  
2.  Na janela **Propriedades**, na propriedade `Size`, defina `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BackColor` com a cor desejada.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
#### Para desenhar um círculo que tenha um preenchimento padronizado  
  
1.  Arraste o controle `OvalShape` da guia **Visual Basic PowerPacks** na **Caixa de Ferramentas** para um controle de contêiner ou formulário.  
  
2.  Na janela **Propriedades**, na propriedade `Size`, defina `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `BackColor` com a cor desejada para o plano de fundo.  
  
4.  Defina a propriedade `BackStyle` como `Opaque`.  
  
5.  Defina a propriedade `FillColor` com a cor desejada para o padrão.  
  
6.  Defina a propriedade `FillStyle` como qualquer valor diferente de `Transparent` ou `Solid`.  
  
#### Para desenhar um círculo que tenha um preenchimento gradual  
  
1.  Arraste o controle `OvalShape` da guia **Visual Basic PowerPacks** na **Caixa de Ferramentas** para um controle de contêiner ou formulário.  
  
2.  Na janela **Propriedades**, na propriedade `Size`, defina `Height` e `Width` como valores iguais.  
  
3.  Defina a propriedade `FillColor` com a cor desejada para a cor inicial.  
  
4.  Defina a propriedade `FillGradientColor` com a cor desejada para a cor final.  
  
5.  Defina a propriedade `FillGradientStyle` como um valor diferente de `None`.  
  
#### Para desenhar um círculo preenchido com uma imagem  
  
1.  Arraste o controle `OvalShape` da guia **Visual Basic PowerPacks** na **Caixa de Ferramentas** para um controle de contêiner ou formulário.  
  
2.  Na janela **Propriedades**, na propriedade `Size`, defina `Height` e `Width` como valores iguais.  
  
3.  Selecione a propriedade `BackgroundImage` e clique no botão **reticências** \(...\).  
  
4.  Na caixa de diálogo **Selecionar Recurso**, selecione uma imagem para exibir.  Se nenhum recurso de imagem estiver listado, clique em **Importar** para navegar até o local de uma imagem.  
  
5.  Clique em **OK** para inserir a imagem.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>   
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>   
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [Como desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)