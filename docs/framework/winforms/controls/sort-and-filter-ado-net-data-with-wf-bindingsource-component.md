---
title: Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032342"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="9e0c5-102">Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e0c5-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="9e0c5-103">Você pode expor a classificação e filtragem de capacidade do <xref:System.Windows.Forms.BindingSource> controlar por meio de <xref:System.Windows.Forms.BindingSource.Sort%2A> e <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="9e0c5-104">Você pode aplicar a classificação simples quando a fonte de dados subjacente é uma <xref:System.ComponentModel.IBindingList>, e você pode aplicar a filtragem e classificação quando a fonte de dados é avançada um <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="9e0c5-105">O <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade requer standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] sintaxe: uma cadeia de caracteres que representa o nome de uma coluna de dados na fonte de dados seguido `ASC` ou `DESC` para indicar se a lista deve ser classificada em ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="9e0c5-106">Você pode definir a classificação avançada ou a classificação em várias colunas separando cada coluna com um separador de vírgula.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="9e0c5-107">O <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade usa uma expressão de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e0c5-108">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9e0c5-109">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9e0c5-110">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9e0c5-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="9e0c5-111">Filtrar os dados com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="9e0c5-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="9e0c5-112">Defina o <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade para a expressão desejada.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="9e0c5-113">No exemplo de código a seguir, a expressão é um nome de coluna seguido pelo valor que você deseja para a coluna.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="9e0c5-114">Classificar os dados com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="9e0c5-114">To sort data with the BindingSource</span></span>  
  
1.  <span data-ttu-id="9e0c5-115">Defina as <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade para o nome da coluna que você deseja seguido por `ASC` ou `DESC` para indicar a ordem de crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2.  <span data-ttu-id="9e0c5-116">Separe múltiplas colunas com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="9e0c5-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e0c5-117">Example</span></span>  
 <span data-ttu-id="9e0c5-118">O exemplo de código a seguir carrega os dados da tabela Customers do banco de dados de exemplo Northwind em um <xref:System.Windows.Forms.DataGridView> controlar e filtra e classifica os dados exibidos.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e0c5-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9e0c5-119">Compiling the Code</span></span>  
 <span data-ttu-id="9e0c5-120">Para executar este exemplo, cole o código em um formulário que contém um <xref:System.Windows.Forms.BindingSource> nomeado `BindingSource1` e uma <xref:System.Windows.Forms.DataGridView> denominada `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="9e0c5-121">Lidar com o <xref:System.Windows.Forms.Form.Load> eventos para o formulário e chame `InitializeSortedFilteredBindingSource` no método do manipulador de eventos de carga.</span><span class="sxs-lookup"><span data-stu-id="9e0c5-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0c5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e0c5-122">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [<span data-ttu-id="9e0c5-123">Como instalar bancos de dados de exemplo</span><span class="sxs-lookup"><span data-stu-id="9e0c5-123">How to: Install Sample Databases</span></span>](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [<span data-ttu-id="9e0c5-124">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="9e0c5-124">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
