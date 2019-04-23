---
title: 'Como: Associar dados ao controle DataGridView do Windows Forms'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160064"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Como: Associar dados ao controle DataGridView do Windows Forms

O <xref:System.Windows.Forms.DataGridView> controle é compatível com o modelo de associação de dados do Windows Forms padrão, para que ele possa se associar a uma variedade de fontes de dados. Normalmente, você associa a um <xref:System.Windows.Forms.BindingSource> que gerencia a interação com a fonte de dados. O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados do Windows Forms, que oferece excelente flexibilidade ao escolher ou modificar a localização dos seus dados. Para obter mais informações sobre fontes de dados do <xref:System.Windows.Forms.DataGridView> controle dá suporte, consulte a [visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md).  

O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView. Para obter mais informações, confira [Como: Associar dados ao controle DataGridView do Windows Forms usando o Designer](bind-data-to-the-datagrid-using-the-designer.md).  

Para se conectar a um controle DataGridView aos dados:

1. Implemente um método para manipular os detalhes de recuperar os dados. O seguinte exemplo de código implementa um `GetData` método que inicializa um <xref:System.Data.SqlClient.SqlDataAdapter>e o utiliza para preencher um <xref:System.Data.DataTable>. Ele então liga o <xref:System.Data.DataTable> para o <xref:System.Windows.Forms.BindingSource>. 

2. Do formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos, associar a <xref:System.Windows.Forms.DataGridView> o controle para o <xref:System.Windows.Forms.BindingSource>e chamar o `GetData` método para recuperar os dados.  

## <a name="example"></a>Exemplo

Este exemplo de código completo recupera dados de um banco de dados para popular um controle DataGridView em um formulário do Windows. O formulário também tem botões para recarregar os dados e enviar alterações para o banco de dados.  

Este exemplo requer: 

- Acesso a um banco de dados de exemplo Northwind do SQL Server. Para obter mais informações sobre como instalar o banco de dados de exemplo Northwind, consulte [obter os bancos de dados de exemplo para exemplos de código ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Referências aos assemblies System, System, System. Data e System. XML.  

Para compilar e executar esse exemplo, cole o código para o *Form1* arquivo de código em um novo projeto Windows Forms. Para obter informações sobre a criação do C# ou a linha de comando do Visual Basic, consulte [linha de comando compilando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [compilar da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Preencher o `connectionString` variável no exemplo com os valores para sua conexão de banco de dados de exemplo Northwind do SQL Server. Autenticação do Windows, também chamado de segurança integrada, é uma maneira mais segura para conectar-se ao banco de dados que o armazenamento de uma senha na cadeia de conexão. Para obter mais informações sobre a segurança de conexão, consulte [proteger as informações de conexão](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Exibir dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Proteger as informações de conexão](../../data/adonet/protecting-connection-information.md)
