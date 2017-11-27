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
ms.openlocfilehash: f170250dde2f6db31ed68908936c0e9714a7e846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="65689-102">Como desenhar linhas com o controle LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="65689-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="65689-103">Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle para desenhar linhas horizontais, verticais ou diagonais em um formulário ou o contêiner, em tempo de design e em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="65689-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="65689-104">**Observação** seu computador pode mostrar diferentes nomes ou locais para alguns de usuário do Visual Studio elementos de interface nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="65689-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="65689-105">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="65689-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="65689-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="65689-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="65689-107">Para desenhar uma linha em tempo de design</span><span class="sxs-lookup"><span data-stu-id="65689-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="65689-108">Arraste o <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** arrastar a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="65689-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="65689-109">Arraste o dimensionamento e mover identificadores de tamanho e posição da linha.</span><span class="sxs-lookup"><span data-stu-id="65689-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="65689-110">Você também pode dimensionar e posicionar a linha alterando o `X1`, `X2`, `Y1`, e `Y2` propriedades no **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="65689-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="65689-111">No **propriedades** janela, opcionalmente, definir propriedades adicionais, como `BorderStyle` ou `BorderColor` para alterar a aparência da linha.</span><span class="sxs-lookup"><span data-stu-id="65689-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="65689-112">Para desenhar uma linha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="65689-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="65689-113">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="65689-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="65689-114">No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="65689-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="65689-115">No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="65689-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="65689-116">Adicione o seguinte código em um procedimento do `Event`:</span><span class="sxs-lookup"><span data-stu-id="65689-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="65689-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65689-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="65689-118">Introdução aos controles de linha e forma</span><span class="sxs-lookup"><span data-stu-id="65689-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="65689-119">Como desenhar formas com os controles OvalShape e RectangleShape</span><span class="sxs-lookup"><span data-stu-id="65689-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
