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
ms.openlocfilehash: e6cdc7f0d54d54448a7b9ed42603b07c93eba719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668334"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Quando usar um ComboBox dos Windows Forms em vez de um ListBox
O <xref:System.Windows.Forms.ComboBox> e o <xref:System.Windows.Forms.ListBox> controles têm comportamentos semelhantes e, em alguns casos, podem ser intercambiáveis. No entanto, há vezes, em que um ou outro é mais apropriado para uma tarefa.  
  
 Em geral, uma caixa de combinação é apropriada quando há uma lista das opções sugeridas e uma caixa de listagem é apropriada quando você deseja limitar a entrada para o que está na lista. Uma caixa de combinação contém um campo de caixa de texto, portanto, as opções que não estão na lista podem ser digitadas. A exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. Nesse caso, o controle selecionará um item se você digitar sua primeira letra.  
  
 Além disso, caixas de combinação economizam espaço em um formulário. Como a lista completa não é exibida até que o usuário clique na seta para baixo, uma caixa de combinação pode se encaixar facilmente em um pequeno espaço em que uma caixa de listagem não caberia. Uma exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.Simple>: a lista completa é exibida e a caixa de combinação ocupa mais espaço do que uma caixa de listagem.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Como: Adicionar e remover itens de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Como: Classificar o conteúdo de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Controles dos Windows Forms usados para listar opções](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
