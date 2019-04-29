---
title: 'Como: Habilitar AutoComplete em controles ToolStrip nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: d7919bf87444ef6c4a64ee236356e762da14853f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941473"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="8cda1-102">Como: Habilitar AutoComplete em controles ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8cda1-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="8cda1-103">O procedimento a seguir combina uma <xref:System.Windows.Forms.ToolStripLabel> com um <xref:System.Windows.Forms.ToolStripComboBox> que podem ser descartados para baixo mostrar uma lista de itens, tais como recentemente visitados sites da Web.</span><span class="sxs-lookup"><span data-stu-id="8cda1-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="8cda1-104">Se o usuário digita um caractere que corresponde ao primeiro caractere de um dos itens na lista, o item é exibido imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8cda1-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cda1-105">O preenchimento automático funciona com `ToolStrip` controles da mesma forma que ele funciona com controles tradicionais, como <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8cda1-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="8cda1-106">Para habilitar AutoComplete em um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8cda1-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="8cda1-107">Criar um <xref:System.Windows.Forms.ToolStrip> controlar e adicionar itens a ele.</span><span class="sxs-lookup"><span data-stu-id="8cda1-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. <span data-ttu-id="8cda1-108">Defina as <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriedade do rótulo e a caixa de combinação para <xref:System.Windows.Forms.ToolStripItemOverflow.Never> para que a lista está sempre disponível, independentemente do tamanho do formulário.</span><span class="sxs-lookup"><span data-stu-id="8cda1-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. <span data-ttu-id="8cda1-109">Adicione palavras à coleção de itens a <xref:System.Windows.Forms.ToolStripComboBox> controle.</span><span class="sxs-lookup"><span data-stu-id="8cda1-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="8cda1-110">Defina as <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> propriedade da caixa de combinação para <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span><span class="sxs-lookup"><span data-stu-id="8cda1-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="8cda1-111">Defina as <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> propriedade da caixa de combinação para <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span><span class="sxs-lookup"><span data-stu-id="8cda1-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8cda1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cda1-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="8cda1-113">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8cda1-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="8cda1-114">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8cda1-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="8cda1-115">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8cda1-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
