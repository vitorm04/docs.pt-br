---
title: "Como desenhar linhas com o controle LineShape (Visual Studio) | Microsoft Docs"
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
  - "linhas, desenho"
  - "Controle LineShape"
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como desenhar linhas com o controle LineShape (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> o controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou recipiente, tanto em tempo de design em tempo de execução.  
  
 **Nota** o computador pode mostrar nomes diferentes ou locais para o usuário Visual Studio alguns elementos de interface nas seguintes instruções.  A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para desenhar uma linha em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar da  **Visual Basic PowerPacks** guia o  **caixa de ferramentas** arraste para um controle de formulário ou recipiente.  
  
2.  Arraste o dimensionamento e mova as alças de dimensionar e posicionar a linha.  
  
     Você também pode dimensionar e posicionar a linha alterando a `X1`, `X2`, `Y1`, e `Y2` propriedades na  **Propriedades** janela.  
  
3.  No  **Propriedades** janela, opcionalmente, defina propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.  
  
### Para desenhar uma linha de tempo de execução  
  
1.  No menu **Project**, escolha **Add Reference**.  
  
2.  No  **Add Reference** caixa de diálogo, selecione  **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em  **OK**.  
  
3.  No  **O Editor de código**, adicionar um `Imports` ou `using` instrução na parte superior do módulo:  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  Adicione o seguinte código em um `Event` procedimento:  
  
     [!code-cs[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>   
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [Como desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)