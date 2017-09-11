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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c1dc1b28c00ffd4e519691e455cdd8ed461ce7b3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="0ece5-102">Como habilitar tabulações entre formas (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0ece5-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="0ece5-103">Controles de linha e forma não tem `TabStop` ou `TabIndex` propriedades, mas você ainda pode habilitar tabulações entre eles.</span><span class="sxs-lookup"><span data-stu-id="0ece5-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="0ece5-104">No exemplo a seguir, pressionar as teclas CTRL e as teclas TAB será guia entre formas. somente da tecla TAB será guia entre os botões.</span><span class="sxs-lookup"><span data-stu-id="0ece5-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ece5-105">Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="0ece5-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="0ece5-106">A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos.</span><span class="sxs-lookup"><span data-stu-id="0ece5-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="0ece5-107">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="0ece5-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="0ece5-108">Para habilitar tabulações entre formas</span><span class="sxs-lookup"><span data-stu-id="0ece5-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="0ece5-109">Arraste três <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>controles e dois <xref:System.Windows.Forms.Button>controles do **Toolbox** a um formulário.</xref:System.Windows.Forms.Button> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape></span><span class="sxs-lookup"><span data-stu-id="0ece5-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="0ece5-110">No **Editor de códigos**, adicione uma `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="0ece5-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="0ece5-111">Adicione o seguinte código em um procedimento de evento:</span><span class="sxs-lookup"><span data-stu-id="0ece5-111">Add the following code in an event procedure:</span></span>  
  
<span data-ttu-id="0ece5-112">[!code-cs[&#1; VbPowerPacksTabbing](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ece5-112">[!code-cs[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]</span></span>  
  
4.  <span data-ttu-id="0ece5-113">Adicione o seguinte código no `Button1_PreviewKeyDown` procedimento de evento:</span><span class="sxs-lookup"><span data-stu-id="0ece5-113">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
<span data-ttu-id="0ece5-114">[!code-cs[N º&2; VbPowerPacksTabbing](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ece5-114">[!code-cs[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ece5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ece5-115">See Also</span></span>  
 <span data-ttu-id="0ece5-116">[Como: desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md) </span><span class="sxs-lookup"><span data-stu-id="0ece5-116">[How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md) </span></span>  
<span data-ttu-id="0ece5-117"> [Como: desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="0ece5-117"> [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md) </span></span>  
<span data-ttu-id="0ece5-118"> [Introdução aos controles de linha e forma](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="0ece5-118"> [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)</span></span>
