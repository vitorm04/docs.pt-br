---
title: 'Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: b2fafdd9959123e27c4b58484281408c3115e4d1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624180"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms
O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados. Os formulários do Windows <xref:System.Windows.Forms.DataGridView> controle torna isso fácil ao expor o <xref:System.Windows.Forms.DataGridView.DataError> evento, que é gerado quando o armazenamento de dados detecta uma violação de restrição ou uma regra de negócio.  
  
 Neste passo a passo, você vai recuperar linhas dos `Customers` de tabela no banco de dados de exemplo Northwind e exibi-las em um <xref:System.Windows.Forms.DataGridView> controle. Quando uma duplicata `CustomerID` valor é detectado em uma nova linha ou uma linha existente editada, a <xref:System.Windows.Forms.DataGridView.DataError> evento ocorrerá, que será tratado exibindo um <xref:System.Windows.Forms.MessageBox> que descreve a exceção.  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Manipular erros que ocorrem durante a entrada de dados em que o Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
- Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Tratar erros de entrada de dados no controle DataGridView  
  
1. Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém uma <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.  
  
     O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.  
  
     Este exemplo de código usa um `GetData` método que retorna um populados <xref:System.Data.DataTable> objeto. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.  
  
    > [!IMPORTANT]
    >  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3. Implemente um manipulador para seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a vinculação de dados.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4. Lidar com o <xref:System.Windows.Forms.DataGridView.DataError> eventos sobre o <xref:System.Windows.Forms.DataGridView>.  
  
     Se o contexto do erro é uma operação de confirmação, exibir o erro em um <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
- Pressione F5 para executar o aplicativo.  
  
     Você verá um <xref:System.Windows.Forms.DataGridView> controle é preenchido com dados da tabela Customers. Se você inserir um valor duplicado para `CustomerID` e confirmar a edição, o valor da célula será revertido automaticamente e você verá um <xref:System.Windows.Forms.MessageBox> que exibe o erro de entrada de dados.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo oferece uma compreensão básica do <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:  
  
- Alterar estilos de borda e cabeçalho. Para obter mais informações, confira [Como: Alterar a borda e estilos de linha de grade no Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Habilitar ou restringir a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, confira [Como: Evitar a adição de linha e exclusão no Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), e [como: Controle DataGridView de tornar as colunas somente leitura no Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Validar a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, confira [Passo a passo: Validando dados em que o Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
- Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, confira [Passo a passo: Implementando o modo Virtual no Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Personalize a aparência das células. Para obter mais informações, confira [Como: Personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [como: Definir estilos de célula padrão para o Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como: Tratar erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Passo a passo: Validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
