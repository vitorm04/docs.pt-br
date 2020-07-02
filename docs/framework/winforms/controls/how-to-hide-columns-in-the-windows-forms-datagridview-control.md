---
title: Ocultar colunas no controle DataGridView
description: Saiba como ocultar colunas programaticamente no controle Windows Forms DataGridView definindo a propriedade DataGridViewColumn. Visible como false.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 27e9f331151acd68d76233bc7dbb09c2d870afde
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618045"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7544f-103">Como ocultar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7544f-103">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7544f-104">Às vezes, você desejará exibir apenas algumas das colunas que estão disponíveis em um <xref:System.Windows.Forms.DataGridView> controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7544f-104">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7544f-105">Por exemplo, talvez você queira mostrar uma coluna salário do funcionário a usuários com credenciais de gerenciamento ao ocultá-lo de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="7544f-105">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="7544f-106">Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém muitas colunas, apenas algumas das quais você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="7544f-106">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="7544f-107">Nesse caso, você normalmente removerá as colunas que não está interessado em Exibir em vez de ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="7544f-107">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="7544f-108">No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> valor da propriedade de uma coluna determina se essa coluna é exibida.</span><span class="sxs-lookup"><span data-stu-id="7544f-108">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="7544f-109">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7544f-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="7544f-110">Consulte também [como: Ocultar colunas no controle Windows Forms DataGridView usando o designer](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7544f-110">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="7544f-111">Para ocultar uma coluna programaticamente</span><span class="sxs-lookup"><span data-stu-id="7544f-111">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="7544f-112">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="7544f-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="7544f-113">Para ocultar uma `CustomerID` coluna gerada automaticamente durante a vinculação de dados, coloque o exemplo de código a seguir em um <xref:System.Windows.Forms.DataGridView.DataBindingComplete> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7544f-113">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7544f-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7544f-114">Compiling the Code</span></span>  
 <span data-ttu-id="7544f-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7544f-115">This example requires:</span></span>  
  
- <span data-ttu-id="7544f-116">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna chamada `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="7544f-116">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="7544f-117">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7544f-117">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7544f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7544f-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7544f-119">Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7544f-119">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="7544f-120">Como remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7544f-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="7544f-121">Como alterar a ordem das colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7544f-121">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
