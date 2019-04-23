---
title: Visão geral do controle ComboBox (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 80056771744c9b97828a024adf32638e545a839e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211563"
---
# <a name="combobox-control-overview-windows-forms"></a>Visão geral do controle ComboBox (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.ComboBox> controle é usado para exibir dados em uma caixa de combinação suspensa. Por padrão, o <xref:System.Windows.Forms.ComboBox> controle aparece em duas partes: a parte superior é uma caixa de texto que permite ao usuário digitar um item de lista. A segunda parte é uma caixa de listagem que exibe uma lista de itens na qual o usuário pode selecionar item. Para obter mais informações sobre outros estilos de caixa de combinação, consulte [Quando usar um ComboBox dos Windows Forms em vez de uma caixa de listagem](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 O <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> propriedade retorna um valor inteiro que corresponde ao item de lista selecionado. Você pode alterar programaticamente o item selecionado, alterando o <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valor em código; o item correspondente na lista será exibida na parte da caixa de texto da caixa de combinação. Se nenhum item for selecionado, o <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valor é -1. Se o primeiro item na lista é selecionado, então o <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valor é 0. O <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriedade é semelhante à <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , mas retorna o item em si, geralmente um valor de cadeia de caracteres. O <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> propriedade reflete o número de itens na lista e o valor da <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> propriedade é sempre um mais do que o maior possível <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valor porque <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> é baseado em zero.  
  
 Para adicionar ou excluir itens em uma <xref:System.Windows.Forms.ComboBox> controlar, use o <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> método. Como alternativa, você pode adicionar itens à lista usando o <xref:System.Windows.Forms.ComboBox.Items%2A> propriedade no designer.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- [Visão geral do controle ListBox](listbox-control-overview-windows-forms.md)
- [Quando usar um ComboBox dos Windows Forms em vez de um ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Como: Adicionar e remover itens de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](add-and-remove-items-from-a-wf-combobox.md)
- [Como: Classificar o conteúdo de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Como: Acessar específicos de itens em um Windows Forms ComboBox, ListBox ou CheckedListBox controle](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Como: Associar um ComboBox dos Windows Forms ou um controle ListBox a dados](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
- [Como: Criar uma tabela de pesquisa para um Windows Forms ComboBox, ListBox ou CheckedListBox controle](create-a-lookup-table-for-a-wf-combobox-listbox.md)
