---
title: Personalizar a classificação em um controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743186"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bb0ab-102">Como personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb0ab-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bb0ab-103">O controle de <xref:System.Windows.Forms.DataGridView> fornece classificação automática, mas, dependendo de suas necessidades, talvez seja necessário personalizar as operações de classificação.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="bb0ab-104">Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="bb0ab-105">Como alternativa, você pode manipular o evento <xref:System.Windows.Forms.DataGridView.SortCompare> ou chamar a sobrecarga `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> para maior flexibilidade de classificação, como classificar várias colunas.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="bb0ab-106">Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="bb0ab-107">Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bb0ab-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="bb0ab-108">Classificação programática</span><span class="sxs-lookup"><span data-stu-id="bb0ab-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="bb0ab-109">O exemplo de código a seguir demonstra uma classificação programática usando as propriedades <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> para determinar a direção da classificação e a propriedade <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> para definir manualmente o glifo de classificação.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="bb0ab-110">A sobrecarga de `Sort(DataGridViewColumn,ListSortDirection)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> é usada para classificar dados somente em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="bb0ab-111">Classificação personalizada usando o evento SortCompare</span><span class="sxs-lookup"><span data-stu-id="bb0ab-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="bb0ab-112">O exemplo de código a seguir demonstra a classificação personalizada usando um manipulador de eventos <xref:System.Windows.Forms.DataGridView.SortCompare>.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="bb0ab-113">A <xref:System.Windows.Forms.DataGridViewColumn> selecionada é classificada e, se houver valores duplicados na coluna, a coluna de ID será usada para determinar a ordem final.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="bb0ab-114">Classificação personalizada usando a interface IComparer</span><span class="sxs-lookup"><span data-stu-id="bb0ab-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="bb0ab-115">O exemplo de código a seguir demonstra a classificação personalizada usando a sobrecarga de `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A>, que usa uma implementação da interface <xref:System.Collections.IComparer> para executar uma classificação de várias colunas.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb0ab-116">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="bb0ab-116">Compiling the Code</span></span>  
 <span data-ttu-id="bb0ab-117">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="bb0ab-117">These examples require:</span></span>  
  
- <span data-ttu-id="bb0ab-118">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="bb0ab-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0ab-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="bb0ab-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="bb0ab-120">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb0ab-120">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bb0ab-121">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb0ab-121">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bb0ab-122">Como definir os modos de classificação para colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb0ab-122">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
