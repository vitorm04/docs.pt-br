---
title: Como associar dados ao controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 4ef9e97745c1c5d7a240e4b07b753b72644c6c15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Como associar dados ao controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle oferece suporte para o modelo de associação de dados formulários do Windows padrão, portanto ele associará a uma variedade de fontes de dados. Na maioria das circunstâncias, no entanto, você associará a uma <xref:System.Windows.Forms.BindingSource> componente que gerenciará os detalhes de interagir com a fonte de dados. O <xref:System.Windows.Forms.BindingSource> componente pode representar qualquer fonte de dados do Windows Forms e oferece excelente flexibilidade ao escolher ou modificar o local de seus dados. Para obter mais informações sobre as fontes de dados com suporte a <xref:System.Windows.Forms.DataGridView> , consulte [visão geral do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Veja também [Como associar dados ao controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>Para conectar um controle DataGridView aos dados  
  
1.  Implementar um método para manipular os detalhes de recuperar dados de um base de dados. O seguinte código exemplo implementa um `GetData` método inicializa um <xref:System.Data.SqlClient.SqlDataAdapter> componente e o utiliza para preencher um <xref:System.Data.DataTable>. O <xref:System.Data.DataTable> é então associado para o <xref:System.Windows.Forms.BindingSource> componente. Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados. Você precisa ter acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server instalado.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  Em sua forma <xref:System.Windows.Forms.Form.Load> manipulador de eventos, a associação a <xref:System.Windows.Forms.DataGridView> controlar para a <xref:System.Windows.Forms.BindingSource> componente e chama o `GetData` método para recuperar os dados do banco de dados.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir fornece botões para recarregar os dados do banco de dados e enviar alterações para o banco de dados.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Windows.Forms, System.Data e System.XML.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
