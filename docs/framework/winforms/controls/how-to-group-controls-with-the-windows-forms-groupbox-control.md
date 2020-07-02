---
title: Controles de grupo com controle GroupBox
description: Saiba como agrupar controles com o Windows Forms controle GroupBox para que você possa criar um agrupamento visual de elementos relacionados.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618058"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="e7557-103">Como agrupar controles com o controle GroupBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7557-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="e7557-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controles são usados para agrupar outros controles.</span><span class="sxs-lookup"><span data-stu-id="e7557-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="e7557-105">Há três razões para agrupar controles:</span><span class="sxs-lookup"><span data-stu-id="e7557-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="e7557-106">Para criar um agrupamento visual dos elementos de formulário relacionados para uma interface do usuário clara.</span><span class="sxs-lookup"><span data-stu-id="e7557-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="e7557-107">Para criar um agrupamento programático (de botões de opção, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="e7557-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="e7557-108">Para mover os controles como uma unidade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e7557-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="e7557-109">Para criar um grupo de controles</span><span class="sxs-lookup"><span data-stu-id="e7557-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="e7557-110">Desenhe um <xref:System.Windows.Forms.GroupBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="e7557-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="e7557-111">Adicione outros controles à caixa de grupo desenhando cada um deles dentro da caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="e7557-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="e7557-112">Se você tiver controles existentes que deseja incluir em uma caixa de grupo, poderá selecionar todos os controles, recortá-los para a área de transferência, selecionar o <xref:System.Windows.Forms.GroupBox> controle e, em seguida, colá-los na caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="e7557-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="e7557-113">Você também pode arrastá-los para a caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="e7557-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="e7557-114">Defina a <xref:System.Windows.Forms.GroupBox.Text%2A> propriedade da caixa de grupo como uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="e7557-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7557-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7557-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="e7557-116">Controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="e7557-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
