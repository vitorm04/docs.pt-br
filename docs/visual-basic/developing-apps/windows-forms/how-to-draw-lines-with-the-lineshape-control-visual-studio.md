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
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="bd758-102">Como: Desenhar linhas com o controle LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="bd758-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="bd758-103">Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou contêiner, em tempo de design e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd758-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="bd758-104">**Observação** seu computador pode mostrar diferentes nomes ou localizações para alguns dos usuário do Visual Studio elementos de interface nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="bd758-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="bd758-105">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="bd758-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="bd758-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="bd758-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="bd758-107">Para desenhar uma linha em tempo de design</span><span class="sxs-lookup"><span data-stu-id="bd758-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="bd758-108">Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** arraste para um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="bd758-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="bd758-109">Arraste o dimensionamento e mova as alças para dimensionar e posicionar a linha.</span><span class="sxs-lookup"><span data-stu-id="bd758-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="bd758-110">Você também pode dimensionar e posicionar a linha, alterando a `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="bd758-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="bd758-111">No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.</span><span class="sxs-lookup"><span data-stu-id="bd758-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="bd758-112">Para desenhar uma linha em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bd758-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="bd758-113">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="bd758-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="bd758-114">No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bd758-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="bd758-115">No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="bd758-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="bd758-116">Adicione o seguinte código em um procedimento do `Event`:</span><span class="sxs-lookup"><span data-stu-id="bd758-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bd758-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd758-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [<span data-ttu-id="bd758-118">Introdução aos controles de linha e forma</span><span class="sxs-lookup"><span data-stu-id="bd758-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="bd758-119">Como: Desenhar formas com os controles OvalShape e RectangleShape</span><span class="sxs-lookup"><span data-stu-id="bd758-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
