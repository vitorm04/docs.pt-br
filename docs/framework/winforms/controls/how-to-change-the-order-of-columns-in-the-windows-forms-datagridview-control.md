---
title: Como alterar a ordem de colunas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: f3b1ddd583f76ab135d13108f8c62775ab894c83
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880283"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="49242-102">Como alterar a ordem de colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49242-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="49242-103">Quando você usa um <xref:System.Windows.Forms.DataGridView> para exibir dados de uma fonte de dados, as colunas no esquema da fonte de dados, às vezes, não aparecem na ordem em que você gostaria de exibi-los.</span><span class="sxs-lookup"><span data-stu-id="49242-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="49242-104">Você pode alterar a ordem das colunas exibida usando o <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> propriedade do <xref:System.Windows.Forms.DataGridViewColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="49242-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="49242-105">O exemplo de código a seguir reposiciona algumas das colunas geradas automaticamente ao se associar à tabela Clientes no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="49242-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="49242-106">Para obter mais informações sobre como associar o <xref:System.Windows.Forms.DataGridView> controle a uma tabela de banco de dados, consulte [como: associar dados ao controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="49242-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="49242-107">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49242-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="49242-108">Veja também [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer](https://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="49242-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="49242-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49242-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49242-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="49242-110">Compiling the Code</span></span>  
 <span data-ttu-id="49242-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="49242-111">This example requires:</span></span>  
  
-   <span data-ttu-id="49242-112">Um <xref:System.Windows.Forms.DataGridView> controle chamado `customersDataGridView` que é associado a uma tabela com os nomes de coluna indicada, como o `Customers` tabela no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="49242-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="49242-113">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, e <xref:System.Xml?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="49242-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49242-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49242-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="49242-115">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49242-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="49242-116">Como associar dados ao controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49242-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
