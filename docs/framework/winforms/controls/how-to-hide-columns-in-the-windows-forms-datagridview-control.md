---
title: Como ocultar colunas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 2ddf4b0701ea563465ca3023c73f588f4e0f3a5f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504572"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f3a12-102">Como ocultar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a12-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f3a12-103">Às vezes você desejará exibir somente algumas das colunas que estão disponíveis em um Windows Forms <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="f3a12-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f3a12-104">Por exemplo, você talvez queira mostrar um funcionário a coluna de salário para usuários com credenciais de gerenciamento enquanto a oculta de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="f3a12-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="f3a12-105">Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém várias colunas, que apenas algumas das quais você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="f3a12-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="f3a12-106">Nesse caso, você normalmente removerá as colunas que você não estiver interessado em Exibir em vez de ocultá-los.</span><span class="sxs-lookup"><span data-stu-id="f3a12-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="f3a12-107">No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> valor da propriedade de uma coluna determina se essa coluna é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3a12-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="f3a12-108">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3a12-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f3a12-109">Consulte também [como: ocultar colunas no Windows Forms DataGridView controle usando o Designer](https://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f3a12-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="f3a12-110">Para ocultar uma coluna de forma programática</span><span class="sxs-lookup"><span data-stu-id="f3a12-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="f3a12-111">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="f3a12-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="f3a12-112">Para ocultar uma `CustomerID` coluna que é gerada automaticamente durante a associação de dados, coloque o seguinte exemplo de código em um <xref:System.Windows.Forms.DataGridView.DataBindingComplete> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f3a12-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3a12-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f3a12-113">Compiling the Code</span></span>  
 <span data-ttu-id="f3a12-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f3a12-114">This example requires:</span></span>  
  
-   <span data-ttu-id="f3a12-115">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="f3a12-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="f3a12-116">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3a12-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a12-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3a12-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f3a12-118">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a12-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="f3a12-119">Como remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a12-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="f3a12-120">Como alterar a ordem de colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a12-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
