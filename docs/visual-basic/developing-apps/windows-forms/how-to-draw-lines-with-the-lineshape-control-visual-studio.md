---
title: 'Como: desenhar linhas com o controle LineShape (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- LineShape control
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 331d87d3f88b14d939ea0877989af574f6725a13
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Como desenhar linhas com o controle LineShape (Visual Studio)
Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape>controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou contêiner, em tempo de design e tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
  
 **Observação** seu computador pode mostrar diferentes nomes ou localizações para alguns dos usuário do Visual Studio elementos de interface nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-draw-a-line-at-design-time"></a>Para desenhar uma linha em tempo de design  
  
1.  Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape>controlar do **Visual Basic PowerPacks** guia o **Toolbox** arrastar a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
  
2.  Arraste o dimensionamento e mova as alças para redimensionar e posicionar a linha.  
  
     Você também pode redimensionar e posicionar a linha alterando o `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.  
  
3.  No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.  
  
### <a name="to-draw-a-line-at-run-time"></a>Para desenhar uma linha em tempo de execução  
  
1.  Sobre o **projeto** menu, clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.  
  
3.  No **Editor de códigos**, adicione uma `Imports` ou `using` instrução na parte superior do módulo:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```cs  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Adicione o seguinte código em um procedimento do `Event`:  
  
     [!code-cs[&#1; VbPowerPacksLine](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksLine n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape></xref:Microsoft.VisualBasic.PowerPacks.LineShape>   
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [Como desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
