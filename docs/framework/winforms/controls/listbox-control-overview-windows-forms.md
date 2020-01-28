---
title: Visão geral do controle ListBox
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745185"
---
# <a name="listbox-control-overview-windows-forms"></a>Visão geral do controle ListBox (Windows Forms)
Um controle de <xref:System.Windows.Forms.ListBox> de Windows Forms exibe uma lista da qual o usuário pode selecionar um ou mais itens. Se o número total de itens exceder o número que pode ser exibido, uma barra de rolagem será adicionada automaticamente ao controle de <xref:System.Windows.Forms.ListBox>. Quando a propriedade <xref:System.Windows.Forms.ListBox.MultiColumn%2A> é definida como `true`, a caixa de listagem exibe itens em várias colunas e uma barra de rolagem horizontal é exibida. Quando a propriedade <xref:System.Windows.Forms.ListBox.MultiColumn%2A> é definida como `false`, a caixa de listagem exibe itens em uma única coluna e uma barra de rolagem vertical é exibida. Quando <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> é definido como `true`, a barra de rolagem aparece independentemente do número de itens. A propriedade <xref:System.Windows.Forms.ListBox.SelectionMode%2A> determina quantos itens de lista podem ser selecionados por vez.  
  
## <a name="ways-to-change-the-listbox-control"></a>Maneiras de alterar o controle ListBox  
 A propriedade <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> retorna um valor inteiro que corresponde ao primeiro item selecionado na caixa de listagem. Você pode alterar programaticamente o item selecionado alterando o valor de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> no código; o item correspondente na lista aparecerá realçado no formulário do Windows. Se nenhum item for selecionado, o valor de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> será-1. Se o primeiro item da lista for selecionado, o valor de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> será 0. Quando vários itens são selecionados, o valor <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> reflete o item selecionado que aparece primeiro na lista. A propriedade <xref:System.Windows.Forms.ListBox.SelectedItem%2A> é semelhante a <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, mas retorna o item em si, geralmente um valor de cadeia de caracteres. A propriedade <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> reflete o número de itens na lista, e o valor da propriedade <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> é sempre mais um maior que o maior valor de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> possível porque <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> é baseado em zero.  
  
 Para adicionar ou excluir itens de um controle de <xref:System.Windows.Forms.ListBox>, use o método <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>. Como alternativa, você pode adicionar itens à lista usando a propriedade <xref:System.Windows.Forms.ListBox.Items%2A> em tempo de design.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ListBox>
- [Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Como associar um controle ComboBox ou ListBox dos Windows Forms aos dados](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Visão geral do controle ComboBox](combobox-control-overview-windows-forms.md)
- [Visão geral do controle CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
- [Como criar uma tabela de pesquisa para um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
