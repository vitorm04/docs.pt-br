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
ms.openlocfilehash: a4bf0850b28b7101ba76f1c1fedc6633eccb81a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346048"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Passo a passo: Validando dados no controle DataGridView do Windows Forms
Ao exibir a funcionalidade de entrada de dados para usuários, frequentemente é necessário validar os dados inseridos no formulário. O <xref:System.Windows.Forms.DataGridView> classe fornece uma maneira conveniente para executar a validação antes de dados são confirmados no repositório de dados. Você pode validar dados manipulando o <xref:System.Windows.Forms.DataGridView.CellValidating> evento, que é gerado pelo <xref:System.Windows.Forms.DataGridView> quando a célula atual é alterado.  
  
 Neste passo a passo, você vai recuperar linhas dos `Customers` de tabela no banco de dados de exemplo Northwind e exibi-las em um <xref:System.Windows.Forms.DataGridView> controle. Quando um usuário edita uma célula na `CompanyName` coluna e tenta sair da célula, o <xref:System.Windows.Forms.DataGridView.CellValidating> manipulador de eventos irá examinar uma nova cadeia de nome da empresa para garantir que ele é não vazio; se o novo valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impedirá que o cursor do usuário de sair da célula até que uma cadeia de caracteres não vazia seja inserida.  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Validar dados no controle DataGridView dos Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Validar dados inseridos em um DataGridView  
  
1. Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém uma <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.  
  
     O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.  
  
     Este exemplo de código usa um `GetData` método que retorna um populados <xref:System.Data.DataTable> objeto. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.  
  
    > [!IMPORTANT]
    >  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows, também conhecida como segurança integrada, é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. Implemente um manipulador para seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a vinculação de dados.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. Implemente manipuladores para o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.CellValidating> e <xref:System.Windows.Forms.DataGridView.CellEndEdit> eventos.  
  
     O <xref:System.Windows.Forms.DataGridView.CellValidating> manipulador de eventos é onde você possa determinar se o valor de uma célula no `CompanyName` coluna estará vazia. Se o valor da célula falhar na validação, defina as <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriedade do <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> classe para `true`. Isso faz com que o <xref:System.Windows.Forms.DataGridView> controle para impedir que o cursor de sair da célula. Defina o <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> propriedade na linha para uma cadeia de caracteres explicativa. Isso exibirá um ícone de erro com uma ToolTip que contém o texto de erro. No <xref:System.Windows.Forms.DataGridView.CellEndEdit> manipulador de eventos, defina o <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> propriedade na linha para a cadeia de caracteres vazia. O <xref:System.Windows.Forms.DataGridView.CellEndEdit> evento ocorre somente quando a célula sair do modo de edição, ele não pode fazer se a validação falhar.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Compile e execute o aplicativo.  
  
     Você verá uma <xref:System.Windows.Forms.DataGridView> preenchido com dados do `Customers` tabela. Ao clicar duas vezes em uma célula da coluna `CompanyName`, é possível editar o valor. Se você excluir todos os caracteres e pressionar a tecla TAB para sair da célula, o <xref:System.Windows.Forms.DataGridView> impedirá a saída. Quando você digita uma cadeia de caracteres não vazia para a célula, o <xref:System.Windows.Forms.DataGridView> controle permite que você saia da célula.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo oferece uma compreensão básica do <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:  
  
-   Alterar estilos de borda e cabeçalho. Para obter mais informações, confira [Como: Alterar a borda e estilos de linha de grade no Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Habilitar ou restringir a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, confira [Como: Evitar a adição de linha e exclusão no Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), e [como: Controle DataGridView de tornar as colunas somente leitura no Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, confira [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados em que o Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, confira [Passo a passo: Implementando o modo Virtual no Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personalize a aparência das células. Para obter mais informações, confira [Como: Personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [como: Definir estilos de fonte e cor no controle DataGridView dos Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como: Validar dados no controle DataGridView dos Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
