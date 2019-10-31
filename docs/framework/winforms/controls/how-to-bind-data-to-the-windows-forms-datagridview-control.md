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
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="1414d-102">Como associar dados ao controle Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1414d-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="1414d-103">O controle <xref:System.Windows.Forms.DataGridView> dá suporte ao modelo de ligação de dados do Windows Forms padrão, portanto, ele pode ser associado a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="1414d-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="1414d-104">Normalmente, você se associa a um <xref:System.Windows.Forms.BindingSource> que gerencia a interação com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1414d-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="1414d-105">O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados de Windows Forms, o que oferece uma grande flexibilidade ao escolher ou modificar o local de seus dados.</span><span class="sxs-lookup"><span data-stu-id="1414d-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="1414d-106">Para obter mais informações sobre fontes de dados às quais o controle de <xref:System.Windows.Forms.DataGridView> dá suporte, consulte [visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1414d-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="1414d-107">O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView.</span><span class="sxs-lookup"><span data-stu-id="1414d-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="1414d-108">Para obter mais informações, consulte [como associar dados ao controle DataGridView Windows Forms usando o designer](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1414d-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="1414d-109">Para conectar um controle DataGridView aos dados:</span><span class="sxs-lookup"><span data-stu-id="1414d-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="1414d-110">Implemente um método para lidar com os detalhes da recuperação dos dados.</span><span class="sxs-lookup"><span data-stu-id="1414d-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="1414d-111">O exemplo de código a seguir implementa um método `GetData` que inicializa um <xref:System.Data.SqlClient.SqlDataAdapter>e o usa para preencher uma <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1414d-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1414d-112">Em seguida, ele associa o <xref:System.Data.DataTable> ao <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="1414d-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="1414d-113">No manipulador de eventos de <xref:System.Windows.Forms.Form.Load> do formulário, associe o controle de <xref:System.Windows.Forms.DataGridView> à <xref:System.Windows.Forms.BindingSource>e chame o método `GetData` para recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="1414d-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="1414d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1414d-114">Example</span></span>

<span data-ttu-id="1414d-115">Este exemplo de código completo recupera dados de um banco de dado para preencher um controle DataGridView em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="1414d-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="1414d-116">O formulário também tem botões para recarregar os dados e enviar as alterações para ele.</span><span class="sxs-lookup"><span data-stu-id="1414d-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="1414d-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1414d-117">This example requires:</span></span> 

- <span data-ttu-id="1414d-118">Acesso a um banco de dados Northwind SQL Server exemplo.</span><span class="sxs-lookup"><span data-stu-id="1414d-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="1414d-119">Para obter mais informações sobre como instalar o banco de dados de exemplo Northwind, consulte [obter os exemplos de exemplo de ADO.net de código](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1414d-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="1414d-120">Referências ao sistema, System. Windows. Forms, System. Data e assemblies System. xml.</span><span class="sxs-lookup"><span data-stu-id="1414d-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="1414d-121">Para compilar e executar este exemplo, Cole o código no arquivo de código *Form1* em um novo projeto Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1414d-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="1414d-122">Para obter informações sobre como criar C# a partir da linha de comando ou Visual Basic, consulte [criação de linha de comando com CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build na linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="1414d-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="1414d-123">Preencha a variável `connectionString` no exemplo com os valores de sua conexão de banco de dados Northwind SQL Server de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1414d-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="1414d-124">A autenticação do Windows, também chamada de segurança integrada, é uma maneira mais segura de se conectar ao banco de dados do que armazenar uma senha na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="1414d-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="1414d-125">Para obter mais informações sobre segurança de conexão, consulte [proteger informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1414d-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1414d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1414d-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1414d-127">Exibir dados no controle Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1414d-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1414d-128">Proteger informações de conexão</span><span class="sxs-lookup"><span data-stu-id="1414d-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
