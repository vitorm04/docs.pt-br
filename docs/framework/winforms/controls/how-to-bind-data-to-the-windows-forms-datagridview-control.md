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
ms.openlocfilehash: cbcc04625a14ebc23cacfb567951bf8f76f14985
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725097"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="6ae5a-102">Como: Associar dados ao controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ae5a-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="6ae5a-103">O <xref:System.Windows.Forms.DataGridView> controle é compatível com o modelo de associação de dados do Windows Forms padrão, para que ele possa se associar a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="6ae5a-104">Normalmente, você associa a um <xref:System.Windows.Forms.BindingSource> que gerencia a interação com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="6ae5a-105">O <xref:System.Windows.Forms.BindingSource> pode ser qualquer fonte de dados do Windows Forms, que oferece excelente flexibilidade ao escolher ou modificar a localização dos seus dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="6ae5a-106">Para obter mais informações sobre fontes de dados do <xref:System.Windows.Forms.DataGridView> controle dá suporte, consulte a [visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6ae5a-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="6ae5a-107">O Visual Studio tem amplo suporte para vinculação de dados ao controle DataGridView.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="6ae5a-108">Para obter mais informações, confira [Como: Associar dados ao controle DataGridView do Windows Forms usando o Designer](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="6ae5a-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="6ae5a-109">Para se conectar a um controle DataGridView aos dados:</span><span class="sxs-lookup"><span data-stu-id="6ae5a-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="6ae5a-110">Implemente um método para manipular os detalhes de recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="6ae5a-111">O seguinte exemplo de código implementa um `GetData` método que inicializa um <xref:System.Data.SqlClient.SqlDataAdapter>e o utiliza para preencher um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6ae5a-112">Ele então liga o <xref:System.Data.DataTable> para o <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="6ae5a-113">Do formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos, associar a <xref:System.Windows.Forms.DataGridView> o controle para o <xref:System.Windows.Forms.BindingSource>e chamar o `GetData` método para recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="6ae5a-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ae5a-114">Example</span></span>

<span data-ttu-id="6ae5a-115">Este exemplo de código completo recupera dados de um banco de dados para popular um controle DataGridView em um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="6ae5a-116">O formulário também tem botões para recarregar os dados e enviar alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="6ae5a-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6ae5a-117">This example requires:</span></span> 

- <span data-ttu-id="6ae5a-118">Acesso a um banco de dados de exemplo Northwind do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="6ae5a-119">Para obter mais informações sobre como instalar o banco de dados de exemplo Northwind, consulte [obter os bancos de dados de exemplo para exemplos de código ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="6ae5a-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="6ae5a-120">Referências aos assemblies System, System, System. Data e System. XML.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="6ae5a-121">Para compilar e executar esse exemplo, cole o código para o *Form1* arquivo de código em um novo projeto Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="6ae5a-122">Para obter informações sobre a criação do C# ou a linha de comando do Visual Basic, consulte [linha de comando compilando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [compilar da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="6ae5a-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="6ae5a-123">Preencher o `connectionString` variável no exemplo com os valores para sua conexão de banco de dados de exemplo Northwind do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="6ae5a-124">Autenticação do Windows, também chamado de segurança integrada, é uma maneira mais segura para conectar-se ao banco de dados que o armazenamento de uma senha na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="6ae5a-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="6ae5a-125">Para obter mais informações sobre a segurança de conexão, consulte [proteger as informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="6ae5a-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ae5a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ae5a-126">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="6ae5a-127">Exibir dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ae5a-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6ae5a-128">Proteger as informações de conexão</span><span class="sxs-lookup"><span data-stu-id="6ae5a-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
