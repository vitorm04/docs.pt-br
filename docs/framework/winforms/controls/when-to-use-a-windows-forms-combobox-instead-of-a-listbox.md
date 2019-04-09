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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111417"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Quando usar um ComboBox dos Windows Forms em vez de um ListBox
O <xref:System.Windows.Forms.ComboBox> e o <xref:System.Windows.Forms.ListBox> controles têm comportamentos semelhantes e, em alguns casos, podem ser intercambiáveis. No entanto, há vezes, em que um ou outro é mais apropriado para uma tarefa.  
  
 Em geral, uma caixa de combinação é apropriada quando há uma lista das opções sugeridas e uma caixa de listagem é apropriada quando você deseja limitar a entrada para o que está na lista. Uma caixa de combinação contém um campo de caixa de texto, portanto, as opções que não estão na lista podem ser digitadas. A exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. Nesse caso, o controle selecionará um item se você digitar sua primeira letra.  
  
 Além disso, caixas de combinação economizam espaço em um formulário. Como a lista completa não é exibida até que o usuário clique na seta para baixo, uma caixa de combinação pode se encaixar facilmente em um pequeno espaço em que uma caixa de listagem não caberia. Uma exceção é quando o <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> estiver definida como <xref:System.Windows.Forms.ComboBoxStyle.Simple>: a lista completa é exibida e a caixa de combinação ocupa mais espaço do que uma caixa de listagem.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Como: Adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox do Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Como: Classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox do Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
