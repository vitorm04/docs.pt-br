---
title: "Como personalizar a classificação no controle DataGridView dos Windows Forms"
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
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3ea4c7ccd215bed9bd31e0cd5155209fddcc7b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="63924-102">Como personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63924-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="63924-103">O <xref:System.Windows.Forms.DataGridView> controle fornece classificação automática, mas, dependendo de suas necessidades, talvez seja necessário personalizar as operações de classificação.</span><span class="sxs-lookup"><span data-stu-id="63924-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="63924-104">Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa.</span><span class="sxs-lookup"><span data-stu-id="63924-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="63924-105">Como alternativa, você pode manipular o <xref:System.Windows.Forms.DataGridView.SortCompare> chamada ou evento de `Sort(IComparer)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método maior flexibilidade de classificação, como classificar várias colunas.</span><span class="sxs-lookup"><span data-stu-id="63924-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="63924-106">Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada.</span><span class="sxs-lookup"><span data-stu-id="63924-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="63924-107">Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="63924-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="63924-108">Classificação programática</span><span class="sxs-lookup"><span data-stu-id="63924-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="63924-109">O exemplo de código a seguir demonstra uma classificação de programação usando o <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> propriedades para determinar a direção da classificação e o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> propriedade para definir manualmente o glifo de classificação.</span><span class="sxs-lookup"><span data-stu-id="63924-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="63924-110">O `Sort(DataGridViewColumn,ListSortDirection)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método é usado para classificar dados somente em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="63924-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="63924-111">Classificação personalizada usando o evento SortCompare</span><span class="sxs-lookup"><span data-stu-id="63924-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="63924-112">O exemplo de código a seguir demonstra a classificação personalizada usando um <xref:System.Windows.Forms.DataGridView.SortCompare> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="63924-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="63924-113">Selecionado <xref:System.Windows.Forms.DataGridViewColumn> está classificada e, se houver valores duplicados na coluna, a coluna ID é usada para determinar a ordem final.</span><span class="sxs-lookup"><span data-stu-id="63924-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="63924-114">Classificação personalizada usando a interface IComparer</span><span class="sxs-lookup"><span data-stu-id="63924-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="63924-115">O exemplo de código a seguir demonstra a classificação personalizada usando o `Sort(IComparer)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método, que usa uma implementação do <xref:System.Collections.IComparer> para executar uma classificação de várias colunas.</span><span class="sxs-lookup"><span data-stu-id="63924-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63924-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="63924-116">Compiling the Code</span></span>  
 <span data-ttu-id="63924-117">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="63924-117">These examples require:</span></span>  
  
-   <span data-ttu-id="63924-118">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="63924-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="63924-119">Para obter informações sobre como compilar esses exemplos da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="63924-119">For information about building these examples from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="63924-120">Você também pode compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="63924-120">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="63924-121">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="63924-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63924-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63924-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="63924-123">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63924-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="63924-124">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63924-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="63924-125">Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63924-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
