---
title: 'Instruções passo a passo: validando dados no controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 8ad8caef5db13b1f917a6c27da523d3ded915d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540957"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: validando dados no controle DataGridView dos Windows Forms
Ao exibir a funcionalidade de entrada de dados para usuários, frequentemente é necessário validar os dados inseridos no formulário. O <xref:System.Windows.Forms.DataGridView> classe fornece uma maneira conveniente de executar a validação antes de dados são passados para o repositório de dados. Você pode validar dados manipulando o <xref:System.Windows.Forms.DataGridView.CellValidating> evento, que é gerado pelo <xref:System.Windows.Forms.DataGridView> quando a célula atual é alterado.  
  
 Neste passo a passo, você vai recuperar linhas do `Customers` de tabela no banco de dados de exemplo Northwind e exibi-los em um <xref:System.Windows.Forms.DataGridView> controle. Quando um usuário edita uma célula no `CompanyName` coluna e tenta deixar a célula, o <xref:System.Windows.Forms.DataGridView.CellValidating> manipulador de eventos examinará a nova sequência nome da empresa para se certificar de que é não vazio; se o novo valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impedirá o cursor do usuário Deixe a célula até que uma cadeia de caracteres não vazia é inserida.  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como Validar Dados no Controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Validar dados inseridos em um DataGridView  
  
1.  Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.  
  
     O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.  
  
     Este exemplo de código usa um `GetData` método que retorna um preenchida <xref:System.Data.DataTable> objeto. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.  
  
    > [!IMPORTANT]
    >  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows, também conhecida como segurança integrada, é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  Implementar um manipulador para o seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a associação de dados.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  Implementar manipuladores para o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.CellValidating> e <xref:System.Windows.Forms.DataGridView.CellEndEdit> eventos.  
  
     O <xref:System.Windows.Forms.DataGridView.CellValidating> manipulador de eventos é onde você determinar se o valor de uma célula de `CompanyName` coluna estará vazia. Se o valor da célula falhar na validação, defina o <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriedade o <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> de classe para `true`. Isso faz com que o <xref:System.Windows.Forms.DataGridView> controle para evitar que o cursor de sair da célula. Definir o <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> propriedade na linha para uma cadeia de caracteres de explicação. Isso exibirá um ícone de erro com uma ToolTip que contém o texto de erro. No <xref:System.Windows.Forms.DataGridView.CellEndEdit> manipulador de eventos, defina o <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> propriedade na linha para a cadeia de caracteres vazia. O <xref:System.Windows.Forms.DataGridView.CellEndEdit> evento ocorre somente quando a célula sai do modo de edição, ele não pode fazer se a validação falhar.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Compile e execute o aplicativo.  
  
     Você verá um <xref:System.Windows.Forms.DataGridView> preenchido com dados a partir de `Customers` tabela. Ao clicar duas vezes em uma célula da coluna `CompanyName`, é possível editar o valor. Se você excluir todos os caracteres e pressionar a tecla TAB para sair da célula, o <xref:System.Windows.Forms.DataGridView> impede que você sair. Quando você digitar uma cadeia de caracteres não vazia para a célula, o <xref:System.Windows.Forms.DataGridView> controle permite que você saia da célula.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este aplicativo oferece uma compreensão básica do <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:  
  
-   Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Habilitar ou restringir a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, consulte [Instruções passo a passo: identificando erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personalize a aparência das células. Para obter mais informações, consulte [Como Personalizar a Aparência de Células no Controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) e [Como Definir Estilos de Fonte e Cor no Controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Entrada de Dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Como validar dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
