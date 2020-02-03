---
title: Classificar o conteúdo do controle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: dee969d777edf76434622fe632f7e934987a1dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742960"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="2a778-102">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a778-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="2a778-103">Os controles de Windows Forms não são classificados quando eles são associados a dados.</span><span class="sxs-lookup"><span data-stu-id="2a778-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="2a778-104">Para exibir dados classificados, use uma fonte de dados que ofereça suporte à classificação e, em seguida, faça com que a fonte de dados a classifique.</span><span class="sxs-lookup"><span data-stu-id="2a778-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="2a778-105">As fontes de dados que dão suporte à classificação são exibições de dados, gerenciadores de exibição de dados e matrizes classificadas.</span><span class="sxs-lookup"><span data-stu-id="2a778-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="2a778-106">Se o controle não estiver vinculado a dados, você poderá classificá-lo.</span><span class="sxs-lookup"><span data-stu-id="2a778-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="2a778-107">Para classificar a lista</span><span class="sxs-lookup"><span data-stu-id="2a778-107">To sort the list</span></span>  
  
1. <span data-ttu-id="2a778-108">Defina a propriedade `Sorted` como `true`.</span><span class="sxs-lookup"><span data-stu-id="2a778-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="2a778-109">Essa configuração reposiciona todos os itens de lista existentes na ordem classificada.</span><span class="sxs-lookup"><span data-stu-id="2a778-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a778-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a778-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="2a778-111">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a778-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="2a778-112">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a778-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="2a778-113">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="2a778-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="2a778-114">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="2a778-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
