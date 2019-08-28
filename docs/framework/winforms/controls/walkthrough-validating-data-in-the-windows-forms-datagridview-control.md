---
title: 'Passo a passo: Validando dados no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046373"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Passo a passo: Validando dados no controle DataGridView do Windows Forms

Ao exibir a funcionalidade de entrada de dados para usuários, frequentemente é necessário validar os dados inseridos no formulário. A <xref:System.Windows.Forms.DataGridView> classe fornece uma maneira conveniente de executar a validação antes que os dados sejam confirmados no armazenamento de dados. Você pode validar os dados manipulando <xref:System.Windows.Forms.DataGridView.CellValidating> o evento, que é gerado <xref:System.Windows.Forms.DataGridView> pelo quando a célula atual é alterada.

Neste tutorial, você irá recuperar linhas da `Customers` tabela no banco de dados de exemplo Northwind e exibi-las em um <xref:System.Windows.Forms.DataGridView> controle. Quando um usuário edita uma célula na `CompanyName` coluna e tenta sair da célula, o manipulador de <xref:System.Windows.Forms.DataGridView.CellValidating> eventos examina a nova cadeia de caracteres do nome da empresa para certificar-se de que ela não está vazia; se o novo valor for <xref:System.Windows.Forms.DataGridView> uma cadeia de caracteres vazia, o irá impedir o cursor do usuário de sair da célula até que uma cadeia de caracteres não vazia seja inserida.

Para copiar o código deste tópico como uma única listagem, confira [Como: Validar dados no controle](how-to-validate-data-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Validar dados inseridos em um DataGridView

1. Crie uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.

    O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.

    Este exemplo de código usa `GetData` um método que retorna um <xref:System.Data.DataTable> objeto populado. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows, também conhecida como segurança integrada, é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do formulário que inicializa <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.BindingSource> e e define a associação de dados.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implemente manipuladores para <xref:System.Windows.Forms.DataGridView> os eventos <xref:System.Windows.Forms.DataGridView.CellValidating> e <xref:System.Windows.Forms.DataGridView.CellEndEdit> do controle.

    O <xref:System.Windows.Forms.DataGridView.CellValidating> manipulador de eventos é onde você determina se o valor de uma célula `CompanyName` na coluna está vazio. Se o valor da célula falhar na validação, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> defina a propriedade <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> da classe `true`como. Isso faz com <xref:System.Windows.Forms.DataGridView> que o controle impeça o cursor de sair da célula. Defina a <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> Propriedade na linha como uma cadeia de caracteres explicativa. Isso exibirá um ícone de erro com uma ToolTip que contém o texto de erro. No manipulador de <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> <xref:System.Windows.Forms.DataGridView.CellEndEdit> eventos, defina a propriedade na linha como a cadeia de caracteres vazia. O <xref:System.Windows.Forms.DataGridView.CellEndEdit> evento ocorre somente quando a célula sai do modo de edição, o que não pode ser feito se falhar na validação.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Compile e execute o aplicativo.

  Você verá um <xref:System.Windows.Forms.DataGridView> preenchido com dados `Customers` da tabela. Ao clicar duas vezes em uma célula da coluna `CompanyName`, é possível editar o valor. Se você excluir todos os caracteres e pressionar a tecla Tab para sair da célula, o <xref:System.Windows.Forms.DataGridView> impedirá que você saia. Quando você digita uma cadeia de caracteres não vazia na célula, o <xref:System.Windows.Forms.DataGridView> controle permite sair da célula.

## <a name="next-steps"></a>Próximas etapas

Esse aplicativo oferece uma compreensão básica dos <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e o comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:

- Alterar estilos de borda e cabeçalho. Para obter mais informações, confira [Como: Altere os estilos da borda e da linha de grade no](change-the-border-and-gridline-styles-in-the-datagrid.md)controle Windows Forms DataGridView.

- Habilitar ou restringir a entrada do usuário <xref:System.Windows.Forms.DataGridView> para o controle. Para obter mais informações, confira [Como: Impeça a adição e exclusão de linhas no controle](prevent-row-addition-and-deletion-datagridview.md)Windows Forms DataGridView e [como: Tornar as colunas somente leitura no controle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

- Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, confira [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados no controle](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)Windows Forms DataGridView.

- Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, confira [Passo a passo: Implementando o modo virtual no controle](implementing-virtual-mode-wf-datagridview-control.md)Windows Forms DataGridView.

- Personalize a aparência das células. Para obter mais informações, confira [Como: Personalize a aparência das células no controle](customize-the-appearance-of-cells-in-the-datagrid.md) Windows Forms DataGridView e [como: Defina os estilos de fonte e cor no controle](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como: Validar dados no controle Windows Forms DataGridView](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados no controle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
