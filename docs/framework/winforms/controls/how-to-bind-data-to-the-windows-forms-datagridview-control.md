---
title: Como associar dados ao controle Windows Forms DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: bdba8af04cd9473b17d1a28f07ead7cd5bf43698
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139087"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Como associar dados ao controle Windows Forms DataGridView

O controle <xref:System.Windows.Forms.DataGridView> dá suporte ao modelo de ligação de dados do Windows Forms padrão, portanto, ele pode ser associado a uma variedade de fontes de dados. Normalmente, você se associa a um <xref:System.Windows.Forms.BindingSource> que gerencia a interação com a fonte de dados. O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados de Windows Forms, o que oferece uma grande flexibilidade ao escolher ou modificar o local de seus dados. Para obter mais informações sobre fontes de dados às quais o controle de <xref:System.Windows.Forms.DataGridView> dá suporte, consulte [visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md).  

O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView. Para obter mais informações, consulte [como associar dados ao controle DataGridView Windows Forms usando o designer](bind-data-to-the-datagrid-using-the-designer.md).  

Para conectar um controle DataGridView aos dados:

1. Implemente um método para lidar com os detalhes da recuperação dos dados. O exemplo de código a seguir implementa um método `GetData` que inicializa um <xref:System.Data.SqlClient.SqlDataAdapter>e o usa para preencher uma <xref:System.Data.DataTable>. Em seguida, ele associa o <xref:System.Data.DataTable> ao <xref:System.Windows.Forms.BindingSource>. 

2. No manipulador de eventos de <xref:System.Windows.Forms.Form.Load> do formulário, associe o controle de <xref:System.Windows.Forms.DataGridView> à <xref:System.Windows.Forms.BindingSource>e chame o método `GetData` para recuperar os dados.  

## <a name="example"></a>Exemplo

Este exemplo de código completo recupera dados de um banco de dado para preencher um controle DataGridView em um Windows Form. O formulário também tem botões para recarregar os dados e enviar as alterações para ele.  

Este exemplo requer: 

- Acesso a um banco de dados Northwind SQL Server exemplo. Para obter mais informações sobre como instalar o banco de dados de exemplo Northwind, consulte [obter os exemplos de exemplo de ADO.net de código](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Referências ao sistema, System. Windows. Forms, System. Data e assemblies System. xml.  

Para compilar e executar este exemplo, Cole o código no arquivo de código *Form1* em um novo projeto Windows Forms. Para obter informações sobre como criar C# a partir da linha de comando ou Visual Basic, consulte [criação de linha de comando com CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build na linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Preencha a variável `connectionString` no exemplo com os valores de sua conexão de banco de dados Northwind SQL Server de exemplo. A autenticação do Windows, também chamada de segurança integrada, é uma maneira mais segura de se conectar ao banco de dados do que armazenar uma senha na cadeia de conexão. Para obter mais informações sobre segurança de conexão, consulte [proteger informações de conexão](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Exibir dados no controle Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Proteger informações de conexão](../../data/adonet/protecting-connection-information.md)
