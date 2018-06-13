---
title: Como acessar objetos de acesso em uma lista suspensa DataGridViewComboBoxCell dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 2758841031be9ca9f0a5eb5e57165191d6870e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529396"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Como acessar objetos de acesso em uma lista suspensa DataGridViewComboBoxCell dos Windows Forms
Como o <xref:System.Windows.Forms.ComboBox> controle, o <xref:System.Windows.Forms.DataGridViewComboBoxColumn> e <xref:System.Windows.Forms.DataGridViewComboBoxCell> tipos permitem que você adicionar objetos arbitrários às suas listas suspensas. Com esse recurso, você pode representar estados complexos em uma lista suspensa sem a necessidade de armazenar objetos correspondentes em uma coleção separada.  
  
 Ao contrário de <xref:System.Windows.Forms.ComboBox> controle, o <xref:System.Windows.Forms.DataGridView> tipos não têm um <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriedade para recuperar o objeto atualmente selecionado. Em vez disso, você deve definir o <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> propriedade para o nome de uma propriedade em seu objeto de negócios. Quando o usuário faz uma seleção, a propriedade indicada do objeto comercial define a célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade.  
  
 Para recuperar o objeto comercial por meio do valor de célula, a propriedade `ValueMember` deve indicar uma propriedade que retorne uma referência ao objeto comercial em si. Portanto, se o tipo de objeto comercial não estiver sob seu controle, você deverá adicionar essa propriedade estendendo o tipo por meio de herança.  
  
 Os procedimentos a seguir demonstram como preencher uma lista suspensa com objetos de negócios e recuperar os objetos por meio da célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Para adicionar objetos comerciais à lista suspensa  
  
1.  Criar um novo <xref:System.Windows.Forms.DataGridViewComboBoxColumn> e preencher seus <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> coleção. Como alternativa, você pode definir a coluna <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> propriedade para a coleção de objetos de negócios. Nesse caso, no entanto, você não pode adicionar "não atribuído" à lista suspensa sem criar um objeto comercial correspondente em sua coleção.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Definir o <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> e <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> propriedades. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indica a propriedade do objeto comercial para exibir na lista suspensa. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indica a propriedade que retorna uma referência para o objeto comercial.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Certifique-se de que o tipo de objeto de negócios contenha uma propriedade que retorne uma referência à instância atual. Essa propriedade deve ser chamada com o valor atribuído à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> na etapa anterior.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Para recuperar o objeto comercial selecionado no momento  
  
-   Obter a célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade e converta-a para o tipo de objeto de negócios.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Exemplo  
 O exemplo completo demonstra o uso de objetos de negócios em uma lista suspensa. No exemplo, um <xref:System.Windows.Forms.DataGridView> controle está associado a uma coleção de `Task` objetos. Cada objeto `Task` tem uma propriedade `AssignedTo` que indica o objeto `Employee` atualmente atribuído à tarefa. A coluna `Assigned To` exibe o de valor da propriedade `Name` para cada funcionário atribuído ou "não atribuído", se o valor da propriedade `Task.AssignedTo` for `null`.  
  
 Para exibir o comportamento deste exemplo, execute as seguintes etapas:  
  
1.  Altere as atribuições na coluna `Assigned To` selecionando valores diferentes nas listas suspensas ou pressionando CTRL+0 em uma célula de caixa de combinação.  
  
2.  Clique em `Generate Report` para exibir as atribuições atuais. Isso demonstra que uma alteração à coluna `Assigned To` atualiza automaticamente a coleção `tasks`.  
  
3.  Clique em um botão `Request Status` para chamar o método `RequestStatus` do objeto `Employee` atual para aquela linha. Isso demonstra que o objeto selecionado foi recuperado com êxito.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
