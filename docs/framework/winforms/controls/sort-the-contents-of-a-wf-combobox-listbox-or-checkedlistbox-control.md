---
title: Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 8b8f9c7ad0ad7d3bbb7f3eeffd44e555207b82c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="3e79d-102">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e79d-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="3e79d-103">Controles de formulários do Windows não classificados quando elas são associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="3e79d-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="3e79d-104">Para exibir os dados classificados, usar uma fonte de dados que dá suporte à classificação e ter a fonte de dados para classificá-los.</span><span class="sxs-lookup"><span data-stu-id="3e79d-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="3e79d-105">Fontes de dados que dão suporte à classificação são modos de exibição de dados, exibir gerenciadores de dados e classificados matrizes.</span><span class="sxs-lookup"><span data-stu-id="3e79d-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="3e79d-106">Se o controle não está associado a dados, você pode classificá-lo.</span><span class="sxs-lookup"><span data-stu-id="3e79d-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="3e79d-107">Para classificar a lista</span><span class="sxs-lookup"><span data-stu-id="3e79d-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="3e79d-108">Defina a propriedade `Sorted` como `true`.</span><span class="sxs-lookup"><span data-stu-id="3e79d-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="3e79d-109">Essa configuração reposiciona todos os itens existentes na lista em ordem classificada.</span><span class="sxs-lookup"><span data-stu-id="3e79d-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e79d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e79d-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="3e79d-111">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e79d-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="3e79d-112">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e79d-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="3e79d-113">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="3e79d-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="3e79d-114">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="3e79d-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
