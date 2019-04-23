---
title: Visão geral do controle ListBox (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: f70246d4a4d158815ee9662036eca8edeb891d85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104189"
---
# <a name="listbox-control-overview-windows-forms"></a>Visão geral do controle ListBox (Windows Forms)
Um Windows Forms <xref:System.Windows.Forms.ListBox> controle exibe uma lista da qual o usuário pode selecionar um ou mais itens. Se o número total de itens exceder o número que pode ser exibido, uma barra de rolagem é adicionada automaticamente para o <xref:System.Windows.Forms.ListBox> controle. Quando o <xref:System.Windows.Forms.ListBox.MultiColumn%2A> estiver definida como `true`, a caixa de listagem exibirá itens em várias colunas e uma barra de rolagem horizontal é exibida. Quando o <xref:System.Windows.Forms.ListBox.MultiColumn%2A> estiver definida como `false`, a caixa de listagem exibirá itens em uma única coluna e uma barra de rolagem vertical é exibida. Quando <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> é definido como `true`, a barra de rolagem é exibida, independentemente do número de itens. O <xref:System.Windows.Forms.ListBox.SelectionMode%2A> propriedade determina quantos itens de lista podem ser selecionados por vez.  
  
## <a name="ways-to-change-the-listbox-control"></a>Maneiras de alterar o controle ListBox  
 O <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> propriedade retorna um valor inteiro que corresponde ao primeiro item selecionado na caixa de listagem. Você pode alterar programaticamente o item selecionado, alterando o <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valor em código; o item correspondente na lista será exibido realçado no formulário do Windows. Se nenhum item for selecionado, o <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valor é -1. Se o primeiro item na lista é selecionado, o <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valor é 0. Quando vários itens são selecionados, o <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valor reflete o item selecionado que aparece primeiro na lista. O <xref:System.Windows.Forms.ListBox.SelectedItem%2A> propriedade é semelhante à <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, mas retorna o item em si, geralmente um valor de cadeia de caracteres. O <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> propriedade reflete o número de itens na lista e o valor da <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> propriedade é sempre um mais do que o maior possível <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valor porque <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> é baseado em zero.  
  
 Para adicionar ou excluir itens em uma <xref:System.Windows.Forms.ListBox> controlar, use o <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> método. Como alternativa, você pode adicionar itens à lista usando o <xref:System.Windows.Forms.ListBox.Items%2A> propriedade em tempo de design.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListBox>
- [Como: Adicionar e remover itens de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](add-and-remove-items-from-a-wf-combobox.md)
- [Como: Classificar o conteúdo de um Windows Forms ComboBox, ListBox ou CheckedListBox controle](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Como: Associar um ComboBox dos Windows Forms ou um controle ListBox a dados](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Visão geral do controle ComboBox](combobox-control-overview-windows-forms.md)
- [Visão geral do controle CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
- [Como: Criar uma tabela de pesquisa para um Windows Forms ComboBox, ListBox ou CheckedListBox controle](create-a-lookup-table-for-a-wf-combobox-listbox.md)
