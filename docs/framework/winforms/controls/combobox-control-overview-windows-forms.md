---
title: Visão geral do controle ComboBox
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743841"
---
# <a name="combobox-control-overview-windows-forms"></a>Visão geral do controle ComboBox (Windows Forms)
O controle de <xref:System.Windows.Forms.ComboBox> de Windows Forms é usado para exibir dados em uma caixa de combinação suspensa. Por padrão, o controle de <xref:System.Windows.Forms.ComboBox> aparece em duas partes: a parte superior é uma caixa de texto que permite ao usuário digitar um item de lista. A segunda parte é uma caixa de listagem que exibe uma lista de itens na qual o usuário pode selecionar item. Para obter mais informações sobre outros estilos de caixa de combinação, consulte [Quando usar um ComboBox dos Windows Forms em vez de uma caixa de listagem](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 A propriedade <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> retorna um valor inteiro que corresponde ao item de lista selecionado. Você pode alterar programaticamente o item selecionado alterando o valor de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> no código; o item correspondente na lista aparecerá na parte da caixa de texto da caixa de combinação. Se nenhum item for selecionado, o valor de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> será-1. Se o primeiro item da lista for selecionado, o valor de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> será 0. A propriedade <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> é semelhante a <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, mas retorna o item em si, geralmente um valor de cadeia de caracteres. A propriedade <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> reflete o número de itens na lista, e o valor da propriedade <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> é sempre mais um maior que o maior valor de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> possível porque <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> é baseado em zero.  
  
 Para adicionar ou excluir itens de um controle de <xref:System.Windows.Forms.ComboBox>, use o método <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>. Como alternativa, você pode adicionar itens à lista usando a propriedade <xref:System.Windows.Forms.ComboBox.Items%2A> no designer.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- [Visão geral do controle ListBox](listbox-control-overview-windows-forms.md)
- [Quando usar um ComboBox dos Windows Forms em vez de um ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Como acessar itens específicos em um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Como associar um controle ComboBox ou ListBox dos Windows Forms aos dados](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
- [Como criar uma tabela de pesquisa para um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
