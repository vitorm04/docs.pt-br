---
title: Como alterar a ordem de colunas no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2107da50f3b8a569bc329dbb1ae1722141921e11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ae1f1-102">Como alterar a ordem de colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae1f1-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ae1f1-103">Quando você usa um <xref:System.Windows.Forms.DataGridView> para exibir dados de uma fonte de dados, as colunas no esquema da fonte de dados, às vezes, não aparecem na ordem em que deseja exibi-los.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="ae1f1-104">Você pode alterar a ordem das colunas de exibido usando o <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> propriedade o <xref:System.Windows.Forms.DataGridViewColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="ae1f1-105">O exemplo de código a seguir reposiciona algumas das colunas geradas automaticamente ao se associar à tabela Clientes no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="ae1f1-106">Para obter mais informações sobre como associar o <xref:System.Windows.Forms.DataGridView> em uma tabela de banco de dados, consulte [como: associar dados para o controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ae1f1-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="ae1f1-107">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="ae1f1-108">Veja também [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ae1f1-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1f1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae1f1-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae1f1-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ae1f1-110">Compiling the Code</span></span>  
 <span data-ttu-id="ae1f1-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="ae1f1-111">This example requires:</span></span>  
  
-   <span data-ttu-id="ae1f1-112">Um <xref:System.Windows.Forms.DataGridView> controle chamado `customersDataGridView` que está associado a uma tabela com os nomes de coluna indicada, como o `Customers` tabela no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="ae1f1-113">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, e <xref:System.Xml?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="ae1f1-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1f1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1f1-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ae1f1-115">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae1f1-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="ae1f1-116">Como associar dados ao controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae1f1-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
