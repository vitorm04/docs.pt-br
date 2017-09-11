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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 450fccd1319189fbdf88cc4e11f2c04957277bb3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="443fa-102">Como desenhar linhas com o controle LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="443fa-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="443fa-103">Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape>controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou contêiner, em tempo de design e tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="443fa-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="443fa-104">**Observação** seu computador pode mostrar diferentes nomes ou localizações para alguns dos usuário do Visual Studio elementos de interface nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="443fa-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="443fa-105">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="443fa-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="443fa-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="443fa-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="443fa-107">Para desenhar uma linha em tempo de design</span><span class="sxs-lookup"><span data-stu-id="443fa-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="443fa-108">Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape>controlar do **Visual Basic PowerPacks** guia o **Toolbox** arrastar a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="443fa-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="443fa-109">Arraste o dimensionamento e mova as alças para redimensionar e posicionar a linha.</span><span class="sxs-lookup"><span data-stu-id="443fa-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="443fa-110">Você também pode redimensionar e posicionar a linha alterando o `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="443fa-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="443fa-111">No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.</span><span class="sxs-lookup"><span data-stu-id="443fa-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="443fa-112">Para desenhar uma linha em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="443fa-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="443fa-113">Sobre o **projeto** menu, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="443fa-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="443fa-114">No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="443fa-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="443fa-115">No **Editor de códigos**, adicione uma `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="443fa-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="443fa-116">Adicione o seguinte código em um procedimento do `Event`:</span><span class="sxs-lookup"><span data-stu-id="443fa-116">Add the following code in an `Event` procedure:</span></span>  
  
     <span data-ttu-id="443fa-117">[!code-cs[&#1; VbPowerPacksLine](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksLine n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="443fa-117">[!code-cs[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443fa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="443fa-118">See Also</span></span>  
 <span data-ttu-id="443fa-119"><xref:Microsoft.VisualBasic.PowerPacks.LineShape></xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="443fa-119"><xref:Microsoft.VisualBasic.PowerPacks.LineShape></span></span>   
<span data-ttu-id="443fa-120"> [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="443fa-120"> [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md) </span></span>  
<span data-ttu-id="443fa-121"> [Como desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)</span><span class="sxs-lookup"><span data-stu-id="443fa-121"> [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)</span></span>
