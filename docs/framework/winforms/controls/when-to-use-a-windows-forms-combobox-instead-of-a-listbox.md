---
title: ComboBox vs. ListBox
description: Saiba como usar Windows Forms caixa de combinação e Windows Forms caixa de listagem e saiba como saber quando um ou outro é mais apropriado para uma tarefa.
ms.date: 03/30/2017
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174413"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="af765-103">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="af765-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="af765-104">O <xref:System.Windows.Forms.ComboBox> e os <xref:System.Windows.Forms.ListBox> controles têm comportamentos semelhantes e, em alguns casos, podem ser intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="af765-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="af765-105">No entanto, há vezes, em que um ou outro é mais apropriado para uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="af765-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="af765-106">Em geral, uma caixa de combinação é apropriada quando há uma lista das opções sugeridas e uma caixa de listagem é apropriada quando você deseja limitar a entrada para o que está na lista.</span><span class="sxs-lookup"><span data-stu-id="af765-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="af765-107">Uma caixa de combinação contém um campo de caixa de texto, portanto, as opções que não estão na lista podem ser digitadas.</span><span class="sxs-lookup"><span data-stu-id="af765-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="af765-108">A exceção é quando a <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> propriedade é definida como <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> .</span><span class="sxs-lookup"><span data-stu-id="af765-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="af765-109">Nesse caso, o controle selecionará um item se você digitar sua primeira letra.</span><span class="sxs-lookup"><span data-stu-id="af765-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="af765-110">Além disso, caixas de combinação economizam espaço em um formulário.</span><span class="sxs-lookup"><span data-stu-id="af765-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="af765-111">Como a lista completa não é exibida até que o usuário clique na seta para baixo, uma caixa de combinação pode se encaixar facilmente em um pequeno espaço em que uma caixa de listagem não caberia.</span><span class="sxs-lookup"><span data-stu-id="af765-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="af765-112">Uma exceção é quando a <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> propriedade é definida como <xref:System.Windows.Forms.ComboBoxStyle.Simple> : a lista completa é exibida e a caixa de combinação ocupa mais espaço do que uma caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="af765-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af765-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="af765-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="af765-114">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="af765-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="af765-115">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="af765-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="af765-116">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="af765-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
