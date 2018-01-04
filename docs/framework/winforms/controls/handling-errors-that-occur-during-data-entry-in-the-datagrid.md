---
title: "Instruções passo a passo: identificando erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms"
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
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 016a30e4b578ead199124d70cc12f240c74bf370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: identificando erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms
O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados. Windows Forms <xref:System.Windows.Forms.DataGridView> controle torna isso fácil expondo o <xref:System.Windows.Forms.DataGridView.DataError> evento, que é gerado quando o repositório de dados detecta uma violação de restrição ou uma regra de negócio quebrada.  
  
 Neste passo a passo, você vai recuperar linhas do `Customers` de tabela no banco de dados de exemplo Northwind e exibi-los em um <xref:System.Windows.Forms.DataGridView> controle. Quando uma duplicata `CustomerID` for detectado em uma nova linha ou uma linha existente editada, a <xref:System.Windows.Forms.DataGridView.DataError> evento ocorrerá, que será tratado exibindo um <xref:System.Windows.Forms.MessageBox> que descreve a exceção.  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como tratar erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Tratar erros de entrada de dados no controle DataGridView  
  
1.  Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.  
  
     O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.  
  
     Este exemplo de código usa um `GetData` método que retorna um preenchida <xref:System.Data.DataTable> objeto. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.  
  
    > [!IMPORTANT]
    >  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Implementar um manipulador para o seu formulário <xref:System.Windows.Forms.Form.Load> evento que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a associação de dados.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  Manipular o <xref:System.Windows.Forms.DataGridView.DataError> evento no <xref:System.Windows.Forms.DataGridView>.  
  
     Se o contexto do erro é uma operação de confirmação, exibir o erro em um <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Pressione F5 para executar o aplicativo.  
  
     Você verá um <xref:System.Windows.Forms.DataGridView> controle preenchido com dados da tabela Customers. Se você inserir um valor duplicado para `CustomerID` e confirmar a edição, o valor da célula será revertida automaticamente e você verá um <xref:System.Windows.Forms.MessageBox> que exibe o erro de entrada de dados.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este aplicativo oferece uma compreensão básica do <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:  
  
-   Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Habilitar ou restringir a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Validar a entrada do usuário para o <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, consulte [Passo a passo: validando dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Manipule conjuntos de dados muito grandes usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personalize a aparência das células. Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) e [Como definir estilos de célula padrão no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Entrada de Dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Como manipular erros ocorridos durante a entrada de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Passo a passo: validando dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
