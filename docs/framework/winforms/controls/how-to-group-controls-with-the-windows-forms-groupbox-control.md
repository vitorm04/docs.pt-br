---
title: Como agrupar controles com o controle GroupBox dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="b8394-102">Como agrupar controles com o controle GroupBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8394-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="b8394-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controles são usados para agrupar outros controles.</span><span class="sxs-lookup"><span data-stu-id="b8394-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="b8394-104">Há três razões para agrupar controles:</span><span class="sxs-lookup"><span data-stu-id="b8394-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="b8394-105">Para criar um agrupamento visual dos elementos de formulário relacionados para uma interface do usuário clara.</span><span class="sxs-lookup"><span data-stu-id="b8394-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="b8394-106">Para criar um agrupamento programático (de botões de opção, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="b8394-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="b8394-107">Para mover os controles como uma unidade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="b8394-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="b8394-108">Para criar um grupo de controles</span><span class="sxs-lookup"><span data-stu-id="b8394-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="b8394-109">Desenhar um <xref:System.Windows.Forms.GroupBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="b8394-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="b8394-110">Adicione outros controles à caixa de grupo desenhando cada um deles dentro da caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="b8394-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="b8394-111">Se você tiver controles existentes que você deseja incluir em uma caixa de grupo, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.GroupBox> de controle e, em seguida, cole-os na caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="b8394-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="b8394-112">Você também pode arrastá-los para a caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="b8394-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="b8394-113">Definir o <xref:System.Windows.Forms.GroupBox.Text%2A> propriedade da caixa de grupo para uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="b8394-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8394-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8394-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="b8394-115">Controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="b8394-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
