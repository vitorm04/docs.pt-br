---
title: "Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e43a23d632b397889721373471a8fa165052d7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="84077-102">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84077-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="84077-103">Controles de formulários do Windows não classificados quando elas são associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="84077-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="84077-104">Para exibir os dados classificados, usar uma fonte de dados que dá suporte à classificação e ter a fonte de dados para classificá-los.</span><span class="sxs-lookup"><span data-stu-id="84077-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="84077-105">Fontes de dados que dão suporte à classificação são modos de exibição de dados, exibir gerenciadores de dados e classificados matrizes.</span><span class="sxs-lookup"><span data-stu-id="84077-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="84077-106">Se o controle não está associado a dados, você pode classificá-lo.</span><span class="sxs-lookup"><span data-stu-id="84077-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="84077-107">Para classificar a lista</span><span class="sxs-lookup"><span data-stu-id="84077-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="84077-108">Defina a propriedade `Sorted` como `true`.</span><span class="sxs-lookup"><span data-stu-id="84077-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="84077-109">Essa configuração reposiciona todos os itens existentes na lista em ordem classificada.</span><span class="sxs-lookup"><span data-stu-id="84077-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84077-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84077-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="84077-111">Vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84077-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="84077-112">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84077-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="84077-113">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="84077-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="84077-114">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="84077-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
