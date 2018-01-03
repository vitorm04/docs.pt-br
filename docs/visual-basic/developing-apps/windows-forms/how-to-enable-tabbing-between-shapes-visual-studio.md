---
title: "Como habilitar tabulações entre formas (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0b1e8b0378e65becd80324491632ecd8dbffdbbf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="cc128-102">Como habilitar tabulações entre formas (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="cc128-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="cc128-103">Controles de linha e forma não têm `TabStop` ou `TabIndex` propriedades, mas você ainda pode habilitar tabulações entre eles.</span><span class="sxs-lookup"><span data-stu-id="cc128-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="cc128-104">No exemplo a seguir, pressionando o tecla CTRL e as teclas TAB será guia entre formas. pressionando a tecla de guia será guia entre os botões.</span><span class="sxs-lookup"><span data-stu-id="cc128-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc128-105">Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="cc128-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="cc128-106">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="cc128-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="cc128-107">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cc128-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="cc128-108">Para habilitar tabulações entre formas</span><span class="sxs-lookup"><span data-stu-id="cc128-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="cc128-109">Arraste três <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controles e dois <xref:System.Windows.Forms.Button> controla do **caixa de ferramentas** a um formulário.</span><span class="sxs-lookup"><span data-stu-id="cc128-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="cc128-110">No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="cc128-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="cc128-111">Adicione o seguinte código em um procedimento de evento:</span><span class="sxs-lookup"><span data-stu-id="cc128-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="cc128-112">Adicione o seguinte código no `Button1_PreviewKeyDown` procedimento de evento:</span><span class="sxs-lookup"><span data-stu-id="cc128-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cc128-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc128-113">See Also</span></span>  
 [<span data-ttu-id="cc128-114">Como desenhar formas com os controles OvalShape e RectangleShape</span><span class="sxs-lookup"><span data-stu-id="cc128-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="cc128-115">Como desenhar linhas com o controle LineShape</span><span class="sxs-lookup"><span data-stu-id="cc128-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="cc128-116">Introdução aos controles de linha e forma</span><span class="sxs-lookup"><span data-stu-id="cc128-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
