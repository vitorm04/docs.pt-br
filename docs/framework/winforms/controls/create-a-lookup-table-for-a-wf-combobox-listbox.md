---
title: Como criar uma tabela de pesquisa para um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f49a8fbd2cc8ffae94e4dcbbc4babf7c1137cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Como criar uma tabela de pesquisa para um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
Às vezes, é útil exibir dados em um formato amigável em um formulário do Windows Forms, porém, armazene os dados em um formato que seja mais significativo para o programa. Por exemplo, um formulário de pedido de alimentos pode exibir os itens de menu por nome em uma caixa de listagem. No entanto, a tabela de dados que registra a ordem conteria os números de identificação exclusivos que representam os alimentos. As tabelas a seguir mostram um exemplo de como armazenar e exibir dados de formulários de pedidos de alimentos.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Quantidade|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Nome|  
|--------|----------|  
|12|Batata|  
|13|Frango|  
  
 Nesse cenário, uma tabela, **OrderDetailsTable**, armazena as informações reais que serão exibidas e salvas. Porém, para economizar espaço, isso é feito de maneira bastante enigmática. A outra tabela, **ItemTable**, contém apenas informações relacionadas à aparência sobre qual número de ID é equivalente a qual nome de alimento, e nada sobre os pedidos de alimentos.  
  
 O **ItemTable** está conectado a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> controle por meio de três propriedades. A propriedade `DataSource` contém o nome dessa tabela. A propriedade `DisplayMember` contém a coluna de dados da tabela que você deseja exibir no controle (o nome do alimento). A propriedade `ValueMember` contém a coluna de dados dessa tabela com as informações armazenadas (o número de ID).  
  
 O **OrderDetailsTable** está conectado ao controle por sua coleção de associações, acessada por meio de <xref:System.Windows.Forms.Control.DataBindings%2A> propriedade. Ao adicionar um objeto de associação à coleção, uma propriedade de controle será conectada a um membro de dados específico (a coluna de números de ID) em uma fonte de dados (**OrderDetailsTable**). Quando uma seleção é feita no controle, a entrada de formulário será salva nessa tabela.  
  
### <a name="to-create-a-lookup-table"></a>Criar uma tabela de pesquisa  
  
1.  Adicionar um <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> controle no formulário.  
  
2.  Conecte-se à fonte de dados.  
  
3.  Estabeleça uma relação de dados entre as duas tabelas. Consulte [Introdução a Objetos DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Defina as propriedades a seguir. Elas podem ser definidos no código ou no designer.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|A tabela que contém informações sobre qual número de ID é equivalente a qual item. No cenário anterior, isso é `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|A coluna da tabela de fonte de dados a ser exibida no controle. No cenário anterior, isso é `"Name"` (para definir no código, use aspas).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|A coluna da tabela de fonte de dados que contém as informações armazenadas. No cenário anterior, isso é `"ID"` (para definir no código, use aspas).|  
  
5.  Em um procedimento, chame o <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> método o <xref:System.Windows.Forms.ControlBindingsCollection> classe para associar o controle <xref:System.Windows.Forms.ListControl.SelectedValue%2A> propriedade para a tabela que registra a entrada de formulário. Você também pode fazer isso no Designer, em vez de no código, acessando o controle <xref:System.Windows.Forms.Control.DataBindings%2A> propriedade o **propriedades** janela. No cenário anterior, isso é `OrderDetailsTable` e a coluna é `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Vinculação de dados e os Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Visão geral do controle ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Visão geral do controle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Visão geral do controle CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Controles dos Windows Forms usados para listar opções](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
