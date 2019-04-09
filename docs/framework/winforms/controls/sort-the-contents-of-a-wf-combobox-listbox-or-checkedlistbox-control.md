---
title: 'Como: Classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 4db1c133aabe39232a891183356e9c1b712f5cc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150599"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="90015-102">Como: Classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90015-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="90015-103">Controles dos Windows Forms não classificados quando elas são associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="90015-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="90015-104">Para exibir os dados classificados, usar uma fonte de dados que dá suporte à classificação e, em seguida, ter a fonte de dados classificá-los.</span><span class="sxs-lookup"><span data-stu-id="90015-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="90015-105">Fontes de dados que dão suporte à classificação são modos de exibição de dados, exibir gerenciadores de dados e classificados de matrizes.</span><span class="sxs-lookup"><span data-stu-id="90015-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="90015-106">Se o controle não está associado a dados, você pode classificá-los.</span><span class="sxs-lookup"><span data-stu-id="90015-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="90015-107">Para classificar a lista</span><span class="sxs-lookup"><span data-stu-id="90015-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="90015-108">Defina a propriedade `Sorted` como `true`.</span><span class="sxs-lookup"><span data-stu-id="90015-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="90015-109">Essa configuração reposiciona todos os itens existentes na lista em ordem classificada.</span><span class="sxs-lookup"><span data-stu-id="90015-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90015-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90015-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="90015-111">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90015-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="90015-112">Como: Adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90015-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="90015-113">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="90015-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="90015-114">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="90015-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
