---
title: Quando usar um ComboBox dos Windows Forms em vez de um ListBox
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
ms.openlocfilehash: 8a2429049acf1a22edde8d132ece17da4e91f1db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111417"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="b641c-102">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="b641c-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="b641c-103">O <xref:System.Windows.Forms.ComboBox> e o <xref:System.Windows.Forms.ListBox> controles têm comportamentos semelhantes e, em alguns casos, podem ser intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="b641c-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="b641c-104">No entanto, há vezes, em que um ou outro é mais apropriado para uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="b641c-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="b641c-105">Em geral, uma caixa de combinação é apropriada quando há uma lista das opções sugeridas e uma caixa de listagem é apropriada quando você deseja limitar a entrada para o que está na lista.</span><span class="sxs-lookup"><span data-stu-id="b641c-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="b641c-106">Uma caixa de combinação contém um campo de caixa de texto, portanto, as opções que não estão na lista podem ser digitadas.</span><span class="sxs-lookup"><span data-stu-id="b641c-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="b641c-107">A exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="b641c-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="b641c-108">Nesse caso, o controle selecionará um item se você digitar sua primeira letra.</span><span class="sxs-lookup"><span data-stu-id="b641c-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="b641c-109">Além disso, caixas de combinação economizam espaço em um formulário.</span><span class="sxs-lookup"><span data-stu-id="b641c-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="b641c-110">Como a lista completa não é exibida até que o usuário clique na seta para baixo, uma caixa de combinação pode se encaixar facilmente em um pequeno espaço em que uma caixa de listagem não caberia.</span><span class="sxs-lookup"><span data-stu-id="b641c-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="b641c-111">Uma exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.Simple>: a lista completa é exibida e a caixa de combinação ocupa mais espaço do que uma caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="b641c-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b641c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b641c-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="b641c-113">Como: Adicionar e remover itens de um Windows Forms ComboBox, ListBox ou CheckedListBox controle</span><span class="sxs-lookup"><span data-stu-id="b641c-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="b641c-114">Como: Classificar o conteúdo de um Windows Forms ComboBox, ListBox ou CheckedListBox controle</span><span class="sxs-lookup"><span data-stu-id="b641c-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="b641c-115">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="b641c-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
