---
title: 'Passo a passo: Criar um controle não associado DataGridView do Windows Forms'
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
ms.openlocfilehash: ba821b461434cb7a5247d2962a161a1c171bbd14
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651472"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Passo a passo: Criar um controle não associado DataGridView do Windows Forms
Você pode querer exibir com frequência dados tabulares que não se originam de um banco de dados. Por exemplo, você talvez queira mostrar o conteúdo de uma matriz bidimensional de cadeias de caracteres. O <xref:System.Windows.Forms.DataGridView> classe fornece uma maneira fácil e altamente personalizável para exibir dados sem associação a uma fonte de dados. Este passo a passo mostra como preencher um <xref:System.Windows.Forms.DataGridView> controlar e gerenciar a adição e exclusão de linhas no modo "não associado". Por padrão, o usuário pode adicionar novas linhas. Para evitar a adição de linha, defina a <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> é de propriedade `false`.  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Criar um controle de DataGridView não associado do Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Para usar um controle DataGridView não associado  
  
1. Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém as seguintes declarações de variável e `Main` método.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implemente um método `SetupLayout` na definição de classe do formulário para configurar o layout do formulário.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Criar uma `SetupDataGridView` método para configurar o <xref:System.Windows.Forms.DataGridView> colunas e propriedades.  
  
     Esse método primeiro adiciona o <xref:System.Windows.Forms.DataGridView> controle no formulário <xref:System.Windows.Forms.Control.Controls%2A> coleção. Em seguida, o número de colunas a serem exibidas é definido usando o <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> propriedade. O estilo padrão para os cabeçalhos de coluna é definido Configurando as <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, e <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> retornado pelo <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> propriedade.  
  
     Propriedades de aparência e layout são definidas e, em seguida, os nomes de coluna são atribuídos. Quando esse método é encerrado, o <xref:System.Windows.Forms.DataGridView> controle está pronto para ser preenchido.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Criar uma `PopulateDataGridView` método para adicionar linhas para o <xref:System.Windows.Forms.DataGridView> controle.  
  
     Cada linha representa uma música e suas informações associadas.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Com os métodos de utilitário em vigor, você pode anexar manipuladores de eventos.  
  
     Você manipulará as **Add** e **excluir** dos botões <xref:System.Windows.Forms.Control.Click> eventos, o formulário <xref:System.Windows.Forms.Form.Load> evento e o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.CellFormatting> eventos.  
  
     Quando o **Add** do botão <xref:System.Windows.Forms.Control.Click> é gerado, uma linha nova e vazia é adicionada para o <xref:System.Windows.Forms.DataGridView>.  
  
     Quando o **exclua** do botão <xref:System.Windows.Forms.Control.Click> é gerado, a linha selecionada é excluída, a menos que a linha para novos registros, que permite ao usuário adicionar novas linhas. Esta linha é sempre a última linha no <xref:System.Windows.Forms.DataGridView> controle.  
  
     Quando o formulário <xref:System.Windows.Forms.Form.Load> é gerado, o `SetupLayout`, `SetupDataGridView`, e `PopulateDataGridView` são chamados de métodos de utilitário.  
  
     Quando o <xref:System.Windows.Forms.DataGridView.CellFormatting> é gerado, cada célula no `Date` coluna está formatada como uma data por extenso, a menos que o valor da célula não pode ser analisado.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
- Pressione F5 para executar o aplicativo.  
  
     Você verá uma <xref:System.Windows.Forms.DataGridView> controle que exibe as músicas listadas em `PopulateDataGridView`. Você pode adicionar novas linhas com o botão **Adicionar Linha** e excluir linhas selecionadas com o botão **Excluir Linha**. O não acoplado <xref:System.Windows.Forms.DataGridView> controle é o armazenamento de dados e seus dados são independentes de qualquer origem externa, como um <xref:System.Data.DataSet> ou uma matriz.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo oferece uma compreensão básica do <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:  
  
- Alterar estilos de borda e cabeçalho. Para obter mais informações, confira [Como: Alterar a borda e estilos de linha de grade no Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Habilitar ou restringir a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, confira [Como: Evitar a adição de linha e exclusão no Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), e [como: Controle DataGridView de tornar as colunas somente leitura no Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, confira [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados em que o Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, confira [Passo a passo: Implementando o modo Virtual no Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Personalize a aparência das células. Para obter mais informações, confira [Como: Personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [como: Definir estilos de célula padrão para o Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como: Criar um controle de DataGridView não associado do Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Modos de exibição dos dados no controle DataGridView do Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
