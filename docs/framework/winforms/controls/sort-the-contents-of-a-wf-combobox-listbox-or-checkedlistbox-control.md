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
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
Os controles de Windows Forms não são classificados quando eles são associados a dados. Para exibir dados classificados, use uma fonte de dados que ofereça suporte à classificação e, em seguida, faça com que a fonte de dados a classifique. As fontes de dados que dão suporte à classificação são exibições de dados, gerenciadores de exibição de dados e matrizes classificadas.  
  
 Se o controle não estiver vinculado a dados, você poderá classificá-lo.  
  
### <a name="to-sort-the-list"></a>Para classificar a lista  
  
1. Defina a propriedade `Sorted` como `true`.  
  
     Essa configuração reposiciona todos os itens de lista existentes na ordem classificada.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Vinculação de dados dos Windows Forms](../windows-forms-data-binding.md)
- [Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Quando usar um ComboBox dos Windows Forms em vez de um ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
