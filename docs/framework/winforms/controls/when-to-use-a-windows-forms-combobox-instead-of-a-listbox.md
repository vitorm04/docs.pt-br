---
title: Quando usar um ComboBox dos Windows Forms em vez de um ListBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c4a2886dae3aee147d80957874d0d98714c0ca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="73253-102">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="73253-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="73253-103">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> controles têm comportamento semelhante e, em alguns casos pode ser intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="73253-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="73253-104">No entanto, há vezes, em que um ou outro é mais apropriado para uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="73253-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="73253-105">Em geral, uma caixa de combinação é apropriada quando há uma lista das opções sugeridas e uma caixa de listagem é apropriada quando você deseja limitar a entrada para o que está na lista.</span><span class="sxs-lookup"><span data-stu-id="73253-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="73253-106">Uma caixa de combinação contém um campo de caixa de texto, portanto, as opções que não estão na lista podem ser digitadas.</span><span class="sxs-lookup"><span data-stu-id="73253-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="73253-107">A exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> está definida como <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="73253-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="73253-108">Nesse caso, o controle selecionará um item se você digitar sua primeira letra.</span><span class="sxs-lookup"><span data-stu-id="73253-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="73253-109">Além disso, caixas de combinação economizam espaço em um formulário.</span><span class="sxs-lookup"><span data-stu-id="73253-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="73253-110">Como a lista completa não é exibida até que o usuário clique na seta para baixo, uma caixa de combinação pode se encaixar facilmente em um pequeno espaço em que uma caixa de listagem não caberia.</span><span class="sxs-lookup"><span data-stu-id="73253-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="73253-111">Uma exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> está definida como <xref:System.Windows.Forms.ComboBoxStyle.Simple>: a lista completa é exibida e a caixa de combinação ocupa mais espaço do que uma caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="73253-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73253-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73253-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="73253-113">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73253-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="73253-114">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73253-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="73253-115">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="73253-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
