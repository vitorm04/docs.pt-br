---
title: 'Como: Classificar e filtrar dados ADO.NET com o componente BindingSource do Windows Forms'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960419"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="9c4e9-102">Como: Classificar e filtrar dados ADO.NET com o componente BindingSource do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c4e9-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="9c4e9-103">Você pode expor a capacidade de classificação e filtragem <xref:System.Windows.Forms.BindingSource> de controle por <xref:System.Windows.Forms.BindingSource.Sort%2A> meio <xref:System.Windows.Forms.BindingSource.Filter%2A> das propriedades e.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="9c4e9-104">Você pode aplicar a classificação simples quando a fonte de dados subjacente <xref:System.ComponentModel.IBindingList>for um, e poderá aplicar filtragem e classificação avançada quando a fonte de dados <xref:System.ComponentModel.IBindingListView>for um.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="9c4e9-105">A <xref:System.Windows.Forms.BindingSource.Sort%2A> propriedade requer a sintaxe ADO.NET padrão: uma cadeia de caracteres que representa o nome de uma coluna de dados na fonte `ASC` de `DESC` dados seguida por ou para indicar se a lista deve ser classificada em ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="9c4e9-106">Você pode definir a classificação avançada ou a classificação em várias colunas separando cada coluna com um separador de vírgula.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="9c4e9-107">A <xref:System.Windows.Forms.BindingSource.Filter%2A> propriedade usa uma expressão de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c4e9-108">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9c4e9-109">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9c4e9-110">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9c4e9-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="9c4e9-111">Filtrar os dados com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="9c4e9-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="9c4e9-112">Defina a <xref:System.Windows.Forms.BindingSource.Filter%2A> Propriedade como a expressão desejada.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="9c4e9-113">No exemplo de código a seguir, a expressão é um nome de coluna seguido pelo valor que você deseja para a coluna.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="9c4e9-114">Classificar os dados com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="9c4e9-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="9c4e9-115">Defina a <xref:System.Windows.Forms.BindingSource.Sort%2A> Propriedade como o nome da coluna que você deseja que `ASC` seja `DESC` seguido por ou para indicar a ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="9c4e9-116">Separe múltiplas colunas com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="9c4e9-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c4e9-117">Example</span></span>  
 <span data-ttu-id="9c4e9-118">O exemplo de código a seguir carrega dados da tabela Customers do banco de dados de <xref:System.Windows.Forms.DataGridView> exemplo Northwind em um controle e filtra e classifica os dados exibidos.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c4e9-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9c4e9-119">Compiling the Code</span></span>  
 <span data-ttu-id="9c4e9-120">Para executar este exemplo, Cole o código em um formulário que contenha <xref:System.Windows.Forms.BindingSource> um `BindingSource1` nome e <xref:System.Windows.Forms.DataGridView> um `dataGridView1`nomeado.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="9c4e9-121">Manipule o <xref:System.Windows.Forms.Form.Load> evento para o formulário e chame `InitializeSortedFilteredBindingSource` o método Carregar manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9c4e9-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4e9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c4e9-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="9c4e9-123">[Como: Instalar bancos de dados de exemplo](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c4e9-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="9c4e9-124">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="9c4e9-124">BindingSource Component</span></span>](bindingsource-component.md)
