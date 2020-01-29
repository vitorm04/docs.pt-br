---
title: Ocultar colunas no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 7ac6ccac5c02f014d5aa629956e51675cc60fddc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736566"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="de020-102">Como ocultar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de020-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="de020-103">Às vezes, você desejará exibir apenas algumas das colunas que estão disponíveis em um controle de <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="de020-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="de020-104">Por exemplo, talvez você queira mostrar uma coluna salário do funcionário a usuários com credenciais de gerenciamento ao ocultá-lo de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="de020-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="de020-105">Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém muitas colunas, apenas algumas das quais você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="de020-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="de020-106">Nesse caso, você normalmente removerá as colunas que não está interessado em Exibir em vez de ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="de020-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="de020-107">No controle <xref:System.Windows.Forms.DataGridView>, o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> de uma coluna determina se essa coluna é exibida.</span><span class="sxs-lookup"><span data-stu-id="de020-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="de020-108">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="de020-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="de020-109">Consulte também [como: Ocultar colunas no controle Windows Forms DataGridView usando o designer](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="de020-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="de020-110">Para ocultar uma coluna programaticamente</span><span class="sxs-lookup"><span data-stu-id="de020-110">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="de020-111">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="de020-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="de020-112">Para ocultar uma coluna de `CustomerID` gerada automaticamente durante a vinculação de dados, coloque o exemplo de código a seguir em um manipulador de eventos <xref:System.Windows.Forms.DataGridView.DataBindingComplete>.</span><span class="sxs-lookup"><span data-stu-id="de020-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de020-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="de020-113">Compiling the Code</span></span>  
 <span data-ttu-id="de020-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="de020-114">This example requires:</span></span>  
  
- <span data-ttu-id="de020-115">Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` que contém uma coluna denominada `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="de020-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="de020-116">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de020-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de020-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="de020-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="de020-118">Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de020-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="de020-119">Como remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de020-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="de020-120">Como alterar a ordem das colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de020-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
