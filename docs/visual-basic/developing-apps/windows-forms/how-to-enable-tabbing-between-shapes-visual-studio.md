---
title: "Como: habilitar tabulações entre formas (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Line control, implementing tabbing
- Shape control, implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: 14
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
ms.openlocfilehash: fb36960a056d7bd1fc1fa5d2fe1da63d83d7eee8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Como habilitar tabulações entre formas (Visual Studio)
Controles de linha e forma não tem `TabStop` ou `TabIndex` propriedades, mas você ainda pode habilitar tabulações entre eles. No exemplo a seguir, pressionar as teclas CTRL e as teclas TAB será guia entre formas. somente da tecla TAB será guia entre os botões.  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="to-enable-tabbing-among-shapes"></a>Para habilitar tabulações entre formas  
  
1.  Arraste três <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>controles e dois <xref:System.Windows.Forms.Button>controles do **Toolbox** a um formulário.</xref:System.Windows.Forms.Button> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
  
2.  No **Editor de códigos**, adicione uma `Imports` ou `using` instrução na parte superior do módulo:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Adicione o seguinte código em um procedimento de evento:  
  
[!code-cs[&#1; VbPowerPacksTabbing](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Adicione o seguinte código no `Button1_PreviewKeyDown` procedimento de evento:  
  
[!code-cs[N º&2; VbPowerPacksTabbing](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [Como: desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
