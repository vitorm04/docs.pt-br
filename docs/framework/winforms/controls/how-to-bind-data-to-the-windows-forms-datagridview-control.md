---
title: Vincular dados ao Controle DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182269"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Como: Vincular dados ao controle DataGridView do Windows Forms

O <xref:System.Windows.Forms.DataGridView> controle suporta o modelo padrão de vinculação de dados do Windows Forms, para que ele possa se ligar a uma variedade de fontes de dados. Normalmente, você <xref:System.Windows.Forms.BindingSource> se vincula a um que gerencia a interação com a fonte de dados. O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados do Windows Forms, o que lhe dá grande flexibilidade ao escolher ou modificar a localização de seus dados. Para obter mais informações <xref:System.Windows.Forms.DataGridView> sobre fontes de dados que o controle suporta, consulte a visão geral do [controle do DataGridView](datagridview-control-overview-windows-forms.md).  

O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView. Para obter mais informações, [consulte Como vincular dados ao controle DataGridView do Windows Forms usando o Designer](bind-data-to-the-datagrid-using-the-designer.md).  

Para conectar um controle DataGridView aos dados:

1. Implemente um método para lidar com os detalhes de recuperação dos dados. O exemplo de código `GetData` a seguir implementa um método que inicializa a <xref:System.Data.SqlClient.SqlDataAdapter>, e usa-o para preencher um <xref:System.Data.DataTable>. Em seguida, <xref:System.Data.DataTable> liga <xref:System.Windows.Forms.BindingSource>o ao .

2. No manipulador de <xref:System.Windows.Forms.Form.Load> eventos do <xref:System.Windows.Forms.DataGridView> formulário, <xref:System.Windows.Forms.BindingSource>vincule o `GetData` controle ao e chame o método para recuperar os dados.  

## <a name="example"></a>Exemplo

Este exemplo de código completo recupera dados de um banco de dados para preencher um controle DataGridView em um formulário Windows. O formulário também possui botões para recarregar dados e enviar alterações ao banco de dados.  

Este exemplo requer:

- Acesso a um banco de dados de amostra do Northwind SQL Server. Para obter mais informações sobre a instalação do banco de dados de amostras do Northwind, consulte [Obter os bancos de dados de amostra para amostras de código ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Referências aos conjuntos System.Windows.Forms, System.Data e System.Xml.  

Para construir e executar este exemplo, cole o código no arquivo de código *Form1* em um novo projeto do Windows Forms. Para obter informações sobre a construção a partir da linha de comando C# ou Visual Basic, consulte [a construção da linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build a partir da linha de [comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Preencha `connectionString` a variável no exemplo com os valores para a conexão de banco de dados de amostra do Northwind SQL Server. A autenticação do Windows, também chamada de segurança integrada, é uma maneira mais segura de se conectar ao banco de dados do que armazenar uma senha na seqüência de conexões. Para obter mais informações sobre segurança de conexão, consulte [Proteger informações de conexão](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Exibir dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Proteger informações de conexão](../../data/adonet/protecting-connection-information.md)
