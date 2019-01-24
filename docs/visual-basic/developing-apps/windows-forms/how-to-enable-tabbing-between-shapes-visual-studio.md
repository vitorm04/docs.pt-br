---
title: 'Como: Habilitar tabulações entre formas (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: c47d94317008af57907b747e53bd13ae7ca229f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498275"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Como: Habilitar tabulações entre formas (Visual Studio)
Controles de linha e forma não possuem `TabStop` ou `TabIndex` propriedades, mas você ainda pode habilitar tabulações entre eles. No exemplo a seguir, pressionando as teclas CTRL e as teclas TAB será guia entre formas. somente da tecla TAB será guia entre os botões.  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="to-enable-tabbing-among-shapes"></a>Para habilitar tabulações entre formas  
  
1.  Arraste três <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controles e dois <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** a um formulário.  
  
2.  No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Adicione o seguinte código em um procedimento de evento:  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Adicione o seguinte código no `Button1_PreviewKeyDown` procedimento de evento:  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Como: Desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Como: Desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
