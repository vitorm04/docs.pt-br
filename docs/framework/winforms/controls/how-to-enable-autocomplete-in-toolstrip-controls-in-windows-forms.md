---
title: Como habilitar AutoComplete em controles ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142012"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Como habilitar AutoComplete em controles ToolStrip nos Windows Forms
O procedimento a <xref:System.Windows.Forms.ToolStripLabel> seguir <xref:System.Windows.Forms.ToolStripComboBox> combina um com um que pode ser descartado para mostrar uma lista de itens, como sites recentemente visitados. Se o usuário digita um caractere que corresponde ao primeiro caractere de um dos itens na lista, o item é exibido imediatamente.  
  
> [!NOTE]
> A conclusão `ToolStrip` automática funciona com controles da mesma forma que <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.TextBox>funciona com controles tradicionais como e .  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Para habilitar AutoComplete em um controle ToolStrip  
  
1. Crie <xref:System.Windows.Forms.ToolStrip> um controle e adicione itens a ele.  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. Defina <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> a propriedade do rótulo e <xref:System.Windows.Forms.ToolStripItemOverflow.Never> da caixa de combinação para que a lista esteja sempre disponível independentemente do tamanho do formulário.  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. Adicione palavras à coleção Itens <xref:System.Windows.Forms.ToolStripComboBox> do controle.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Defina <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> a propriedade da <xref:System.Windows.Forms.AutoCompleteMode.Append>caixa de combinação para .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Defina <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> a propriedade da <xref:System.Windows.Forms.AutoCompleteSource.ListItems>caixa de combinação para .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
