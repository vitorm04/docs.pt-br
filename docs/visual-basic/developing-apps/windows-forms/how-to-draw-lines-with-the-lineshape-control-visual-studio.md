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
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="aec25-102">Como desenhar linhas com o controle LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="aec25-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="aec25-103">Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou o contêiner, em tempo de design e em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="aec25-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="aec25-104">**Observação** seu computador pode mostrar diferentes nomes ou locais para alguns de usuário do Visual Studio elementos de interface nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="aec25-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="aec25-105">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="aec25-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="aec25-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="aec25-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="aec25-107">Para desenhar uma linha em tempo de design</span><span class="sxs-lookup"><span data-stu-id="aec25-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="aec25-108">Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** arrastar a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="aec25-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="aec25-109">Arraste o dimensionamento e mover identificadores de tamanho e posição da linha.</span><span class="sxs-lookup"><span data-stu-id="aec25-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="aec25-110">Você também pode dimensionar e posicionar a linha alterando o `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="aec25-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="aec25-111">No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.</span><span class="sxs-lookup"><span data-stu-id="aec25-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="aec25-112">Para desenhar uma linha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="aec25-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="aec25-113">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="aec25-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="aec25-114">No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="aec25-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="aec25-115">No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="aec25-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="aec25-116">Adicione o seguinte código em um procedimento do `Event`:</span><span class="sxs-lookup"><span data-stu-id="aec25-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="aec25-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aec25-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="aec25-118">Introdução aos controles de linha e forma</span><span class="sxs-lookup"><span data-stu-id="aec25-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="aec25-119">Como desenhar formas com os controles OvalShape e RectangleShape</span><span class="sxs-lookup"><span data-stu-id="aec25-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
