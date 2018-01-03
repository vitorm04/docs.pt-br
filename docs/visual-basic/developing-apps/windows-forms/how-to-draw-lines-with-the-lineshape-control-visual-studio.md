---
title: Como desenhar linhas com o controle LineShape (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Como desenhar linhas com o controle LineShape (Visual Studio)
Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou o contêiner, em tempo de design e em tempo de execução.  
  
 **Observação** seu computador pode mostrar diferentes nomes ou locais para alguns de usuário do Visual Studio elementos de interface nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Para desenhar uma linha em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** arrastar a um controle de formulário ou contêiner.  
  
2.  Arraste o dimensionamento e mover identificadores de tamanho e posição da linha.  
  
     Você também pode dimensionar e posicionar a linha alterando o `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.  
  
3.  No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.  
  
### <a name="to-draw-a-line-at-run-time"></a>Para desenhar uma linha de tempo de execução  
  
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
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Como desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
