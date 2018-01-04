---
title: "Passo a passo: Criando um formulário mestre / detalhes usando dois controles DataGridView dos Windows Forms"
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
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af6f1bcb172543b372cbca52f54b675b6baf87d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms
Um dos cenários mais comuns para usar o <xref:System.Windows.Forms.DataGridView> controle é o *mestre/detalhes* formulário, na qual uma relação pai/filho entre duas tabelas de banco de dados é exibida. Seleção de linhas na tabela mestra faz com que a tabela de detalhes sejam atualizadas com os dados filho correspondentes.  
  
 Implementando um formulário mestre/detalhes é fácil de usar a interação entre o <xref:System.Windows.Forms.DataGridView> controle e o <xref:System.Windows.Forms.BindingSource> componente. Neste passo a passo, você criará o formulário usando dois <xref:System.Windows.Forms.DataGridView> controles e dois <xref:System.Windows.Forms.BindingSource> componentes. O formulário mostrará duas tabelas relacionadas no banco de dados de exemplo SQL Server Northwind: `Customers` e `Orders`. Quando você terminar, você terá um formulário que mostra todos os clientes no banco de dados no mestre <xref:System.Windows.Forms.DataGridView> e todos os pedidos do cliente selecionado no detalhe <xref:System.Windows.Forms.DataGridView>.  
  
 Para copiar o código neste tópico como uma única listagem, consulte [Como criar um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.  
  
## <a name="creating-the-form"></a>Criando o formulário  
  
#### <a name="to-create-a-masterdetail-form"></a>Para criar um formulário mestre/detalhes  
  
1.  Criar uma classe que deriva de <xref:System.Windows.Forms.Form> e contém duas <xref:System.Windows.Forms.DataGridView> controles e dois <xref:System.Windows.Forms.BindingSource> componentes. O código a seguir fornece inicialização de formulário básica e inclui um método `Main`. Se você usar o designer [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] para criar o seu formulário, poderá usar o código gerado pelo designer em vez desse código, mas não se esqueça de usar os nomes mostrados nas declarações de variável aqui.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Implemente um método na sua definição de classe do formulário para manipular os detalhes da conexão ao banco de dados. Este exemplo usa um `GetData` método que preenche um <xref:System.Data.DataSet> de objeto, adiciona um <xref:System.Data.DataRelation> objeto para o conjunto de dados e associa o <xref:System.Windows.Forms.BindingSource> componentes. Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados.  
  
    > [!IMPORTANT]
    >  O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Implementar um manipulador para o seu formulário <xref:System.Windows.Forms.Form.Load> evento que associa o <xref:System.Windows.Forms.DataGridView> controles para o <xref:System.Windows.Forms.BindingSource> componentes e chama o `GetData` método. O exemplo a seguir inclui o código que pode ser redimensionada <xref:System.Windows.Forms.DataGridView> colunas para ajustar os dados exibidos.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Compile e execute o aplicativo.  
  
     Você verá dois <xref:System.Windows.Forms.DataGridView> controla um acima do outro. Na parte superior estão os clientes da tabela `Customers` Northwind e na parte inferior estão os `Orders` correspondentes ao cliente selecionado. Conforme você seleciona linhas diferentes na parte superior <xref:System.Windows.Forms.DataGridView>, o conteúdo do canto inferior <xref:System.Windows.Forms.DataGridView> alterar.  
  
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
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Como criar um formulário mestre/detalhado usando dois controles DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
