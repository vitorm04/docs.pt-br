---
title: 'Como: Desenhar linhas com o controle LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 46360c01dfaf2c6fe199725a9ecfba2248c72d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596222"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Como: Desenhar linhas com o controle LineShape (Visual Studio)
Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou contêiner, em tempo de design e tempo de execução.  
  
 **Observação** seu computador pode mostrar diferentes nomes ou localizações para alguns dos usuário do Visual Studio elementos de interface nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Para desenhar uma linha em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** arraste para um controle de formulário ou contêiner.  
  
2.  Arraste o dimensionamento e mova as alças para dimensionar e posicionar a linha.  
  
     Você também pode dimensionar e posicionar a linha, alterando a `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.  
  
3.  No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.  
  
### <a name="to-draw-a-line-at-run-time"></a>Para desenhar uma linha em tempo de execução  
  
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
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Como: Desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
