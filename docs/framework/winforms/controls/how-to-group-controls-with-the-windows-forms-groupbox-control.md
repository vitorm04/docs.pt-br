---
title: 'Como: Agrupar controles com o controle de caixa de grupo do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 44f0116511165c021f8e3dc35fb14e5cfb6f619e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686914"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="f4d89-102">Como: Agrupar controles com o controle de caixa de grupo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4d89-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="f4d89-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controles são usados para agrupar outros controles.</span><span class="sxs-lookup"><span data-stu-id="f4d89-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="f4d89-104">Há três razões para agrupar controles:</span><span class="sxs-lookup"><span data-stu-id="f4d89-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="f4d89-105">Para criar um agrupamento visual dos elementos de formulário relacionados para uma interface do usuário clara.</span><span class="sxs-lookup"><span data-stu-id="f4d89-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="f4d89-106">Para criar um agrupamento programático (de botões de opção, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="f4d89-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="f4d89-107">Para mover os controles como uma unidade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="f4d89-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="f4d89-108">Para criar um grupo de controles</span><span class="sxs-lookup"><span data-stu-id="f4d89-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="f4d89-109">Desenhar um <xref:System.Windows.Forms.GroupBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="f4d89-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="f4d89-110">Adicione outros controles à caixa de grupo desenhando cada um deles dentro da caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="f4d89-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="f4d89-111">Se você tiver controles existentes que você deseja incluir em uma caixa de grupo, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.GroupBox> controlar e, em seguida, cole-os na caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="f4d89-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="f4d89-112">Você também pode arrastá-los para a caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="f4d89-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="f4d89-113">Defina o <xref:System.Windows.Forms.GroupBox.Text%2A> propriedade da caixa de grupo para uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="f4d89-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d89-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4d89-114">See also</span></span>
- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="f4d89-115">Controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="f4d89-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
