---
title: 'Como: associar um objeto de DataView a um controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: cbae5453be485896e27a5039ece20bb3bcec9913
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556974"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="492c5-102">Como: associar um objeto de DataView a um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="492c5-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="492c5-103">O controle de <xref:System.Windows.Forms.DataGridView> fornece uma maneira poderosa e flexível para exibir dados em um formato de tabela.</span><span class="sxs-lookup"><span data-stu-id="492c5-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="492c5-104">O controle de <xref:System.Windows.Forms.DataGridView> oferece suporte ao modelo padrão de associação de dados do Windows Forms, portanto associar-se-&amp;z a <xref:System.Data.DataView> e uma variedade de outras fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="492c5-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="492c5-105">Na maioria das situações, o entanto, você associar-se-&amp;z a um componente de <xref:System.Windows.Forms.BindingSource> que gerencia os detalhes de interagir com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="492c5-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="492c5-106">Para obter mais informações sobre o <xref:System.Windows.Forms.DataGridView> controle, consulte [visão geral do controle DataGridView](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="492c5-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="492c5-107">Para se conectar a um controle DataGridView em um DataView</span><span class="sxs-lookup"><span data-stu-id="492c5-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="492c5-108">Implementar um método para manipular os detalhes de recuperar dados de um base de dados.</span><span class="sxs-lookup"><span data-stu-id="492c5-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="492c5-109">O exemplo de código a seguir implementa um método de `GetData` que inicializa um componente de <xref:System.Data.SqlClient.SqlDataAdapter> e usá-lo para preencher <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="492c5-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="492c5-110">Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados.</span><span class="sxs-lookup"><span data-stu-id="492c5-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="492c5-111">Você precisa ter acesso a um servidor com o base de dados de exemplo AdventureWorks do SQL Server instalado.</span><span class="sxs-lookup"><span data-stu-id="492c5-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="492c5-112">No manipulador de eventos <xref:System.Windows.Forms.Form.Load> do formulário, associar o controle de <xref:System.Windows.Forms.DataGridView> componente de <xref:System.Windows.Forms.BindingSource> e chame o método de `GetData` para recuperar os dados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="492c5-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="492c5-113">O <xref:System.Data.DataView> é criado a partir de um LINQ to DataSet consulta sobre o contato <xref:System.Data.DataTable> e, em seguida, é associado ao <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="492c5-113">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="492c5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="492c5-114">See also</span></span>

- [<span data-ttu-id="492c5-115">Associação e LINQ to DataSet de dados</span><span class="sxs-lookup"><span data-stu-id="492c5-115">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
