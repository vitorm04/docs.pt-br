---
title: Criar um controle DataGridView não associado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740177"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Instruções passo a passo: criando um controle não associado DataGridView dos Windows Forms
Você pode querer exibir com frequência dados tabulares que não se originam de um banco de dados. Por exemplo, você talvez queira mostrar o conteúdo de uma matriz bidimensional de cadeias de caracteres. A classe <xref:System.Windows.Forms.DataGridView> fornece uma maneira fácil e altamente personalizável de exibir dados sem associar a uma fonte de dados. Este tutorial mostra como preencher um controle de <xref:System.Windows.Forms.DataGridView> e gerenciar a adição e a exclusão de linhas no modo "desassociado". Por padrão, o usuário pode adicionar novas linhas. Para evitar a adição de linha, defina a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> é `false`.  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como criar um controle DataGridView não associado do Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Para usar um controle DataGridView não associado  
  
1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha as seguintes declarações de variável e `Main` método.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implemente um método `SetupLayout` na definição de classe do formulário para configurar o layout do formulário.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Crie um método de `SetupDataGridView` para configurar as colunas e propriedades de <xref:System.Windows.Forms.DataGridView>.  
  
     Esse método primeiro adiciona o controle de <xref:System.Windows.Forms.DataGridView> à coleção de <xref:System.Windows.Forms.Control.Controls%2A> do formulário. Em seguida, o número de colunas a serem exibidas é definido usando a propriedade <xref:System.Windows.Forms.DataGridView.ColumnCount%2A>. O estilo padrão para os cabeçalhos de coluna é definido definindo as propriedades <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>e <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> do <xref:System.Windows.Forms.DataGridViewCellStyle> retornado pela propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>.  
  
     Propriedades de aparência e layout são definidas e, em seguida, os nomes de coluna são atribuídos. Quando esse método é encerrado, o controle de <xref:System.Windows.Forms.DataGridView> está pronto para ser populado.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Crie um método de `PopulateDataGridView` para adicionar linhas ao controle de <xref:System.Windows.Forms.DataGridView>.  
  
     Cada linha representa uma música e suas informações associadas.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Com os métodos de utilitário em vigor, você pode anexar manipuladores de eventos.  
  
     Você manipulará os eventos de <xref:System.Windows.Forms.Control.Click> **Adicionar** e **excluir** botões, o evento de <xref:System.Windows.Forms.Form.Load> do formulário e o evento <xref:System.Windows.Forms.DataGridView.CellFormatting> do controle de <xref:System.Windows.Forms.DataGridView>.  
  
     Quando o evento de <xref:System.Windows.Forms.Control.Click> do botão **Adicionar** é gerado, uma nova linha vazia é adicionada à <xref:System.Windows.Forms.DataGridView>.  
  
     Quando o evento de <xref:System.Windows.Forms.Control.Click> do botão de **exclusão** é gerado, a linha selecionada é excluída, a menos que seja a linha de novos registros, o que permite ao usuário adicionar novas linhas. Essa linha é sempre a última linha no controle de <xref:System.Windows.Forms.DataGridView>.  
  
     Quando o evento de <xref:System.Windows.Forms.Form.Load> do formulário é gerado, os métodos do utilitário `SetupLayout`, `SetupDataGridView`e `PopulateDataGridView` são chamados.  
  
     Quando o evento de <xref:System.Windows.Forms.DataGridView.CellFormatting> é gerado, cada célula na coluna `Date` é formatada como uma data longa, a menos que o valor da célula não possa ser analisado.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
- Pressione F5 para executar o aplicativo.  
  
     Você verá um controle de <xref:System.Windows.Forms.DataGridView> que exibe as músicas listadas em `PopulateDataGridView`. Você pode adicionar novas linhas com o botão **Adicionar Linha** e excluir linhas selecionadas com o botão **Excluir Linha**. O controle de <xref:System.Windows.Forms.DataGridView> não associado é o armazenamento de dados e seus dados são independentes de qualquer fonte externa, como um <xref:System.Data.DataSet> ou uma matriz.  
  
## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}  
 Esse aplicativo oferece uma compreensão básica dos recursos do controle de <xref:System.Windows.Forms.DataGridView>. Você pode personalizar a aparência e o comportamento do controle de <xref:System.Windows.Forms.DataGridView> de várias maneiras:  
  
- Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Habilitar ou restringir a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, consulte [Instruções passo a passo: identificando erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Manipule conjuntos de dados muito grandes usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Personalize a aparência das células. Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [Como definir estilos de célula padrão no controle DataGridView dos Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como criar um controle DataGridView não associado dos Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Modos de exibição dos dados no controle DataGridView do Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
