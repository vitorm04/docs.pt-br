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
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="a389c-102">Como: Vincular dados ao controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a389c-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="a389c-103">O <xref:System.Windows.Forms.DataGridView> controle suporta o modelo padrão de vinculação de dados do Windows Forms, para que ele possa se ligar a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="a389c-104">Normalmente, você <xref:System.Windows.Forms.BindingSource> se vincula a um que gerencia a interação com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="a389c-105">O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados do Windows Forms, o que lhe dá grande flexibilidade ao escolher ou modificar a localização de seus dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="a389c-106">Para obter mais informações <xref:System.Windows.Forms.DataGridView> sobre fontes de dados que o controle suporta, consulte a visão geral do [controle do DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a389c-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="a389c-107">O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView.</span><span class="sxs-lookup"><span data-stu-id="a389c-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="a389c-108">Para obter mais informações, [consulte Como vincular dados ao controle DataGridView do Windows Forms usando o Designer](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a389c-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="a389c-109">Para conectar um controle DataGridView aos dados:</span><span class="sxs-lookup"><span data-stu-id="a389c-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="a389c-110">Implemente um método para lidar com os detalhes de recuperação dos dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="a389c-111">O exemplo de código `GetData` a seguir implementa um método que inicializa a <xref:System.Data.SqlClient.SqlDataAdapter>, e usa-o para preencher um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a389c-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a389c-112">Em seguida, <xref:System.Data.DataTable> liga <xref:System.Windows.Forms.BindingSource>o ao .</span><span class="sxs-lookup"><span data-stu-id="a389c-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="a389c-113">No manipulador de <xref:System.Windows.Forms.Form.Load> eventos do <xref:System.Windows.Forms.DataGridView> formulário, <xref:System.Windows.Forms.BindingSource>vincule o `GetData` controle ao e chame o método para recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="a389c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a389c-114">Example</span></span>

<span data-ttu-id="a389c-115">Este exemplo de código completo recupera dados de um banco de dados para preencher um controle DataGridView em um formulário Windows.</span><span class="sxs-lookup"><span data-stu-id="a389c-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="a389c-116">O formulário também possui botões para recarregar dados e enviar alterações ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a389c-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="a389c-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a389c-117">This example requires:</span></span>

- <span data-ttu-id="a389c-118">Acesso a um banco de dados de amostra do Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a389c-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="a389c-119">Para obter mais informações sobre a instalação do banco de dados de amostras do Northwind, consulte [Obter os bancos de dados de amostra para amostras de código ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a389c-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="a389c-120">Referências aos conjuntos System.Windows.Forms, System.Data e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="a389c-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="a389c-121">Para construir e executar este exemplo, cole o código no arquivo de código *Form1* em um novo projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a389c-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="a389c-122">Para obter informações sobre a construção a partir da linha de comando C# ou Visual Basic, consulte [a construção da linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build a partir da linha de [comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="a389c-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="a389c-123">Preencha `connectionString` a variável no exemplo com os valores para a conexão de banco de dados de amostra do Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a389c-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="a389c-124">A autenticação do Windows, também chamada de segurança integrada, é uma maneira mais segura de se conectar ao banco de dados do que armazenar uma senha na seqüência de conexões.</span><span class="sxs-lookup"><span data-stu-id="a389c-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="a389c-125">Para obter mais informações sobre segurança de conexão, consulte [Proteger informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="a389c-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a389c-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="a389c-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a389c-127">Exibir dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a389c-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a389c-128">Proteger informações de conexão</span><span class="sxs-lookup"><span data-stu-id="a389c-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
