---
title: 'Como: Personalizar a classificação no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 0e7dffa45dc8d3ac467129d44a7c73a8c4b4bfa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904326"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f63c-102">Como: Personalizar a classificação no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f63c-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9f63c-103">O <xref:System.Windows.Forms.DataGridView> controle proporciona classificação automática mas, dependendo das suas necessidades, talvez você precise personalizar as operações de classificação.</span><span class="sxs-lookup"><span data-stu-id="9f63c-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="9f63c-104">Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa.</span><span class="sxs-lookup"><span data-stu-id="9f63c-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="9f63c-105">Como alternativa, você pode lidar com o <xref:System.Windows.Forms.DataGridView.SortCompare> chamada ou evento a `Sort(IComparer)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método para maior flexibilidade de classificação, como classificar várias colunas.</span><span class="sxs-lookup"><span data-stu-id="9f63c-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="9f63c-106">Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9f63c-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="9f63c-107">Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f63c-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="9f63c-108">Classificação programática</span><span class="sxs-lookup"><span data-stu-id="9f63c-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="9f63c-109">O exemplo de código a seguir demonstra uma classificação programática usando o <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> propriedades para determinar a direção da classificação e o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> propriedade para definir manualmente o glifo de classificação.</span><span class="sxs-lookup"><span data-stu-id="9f63c-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="9f63c-110">O `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método é usado para classificar dados somente em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="9f63c-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="9f63c-111">Classificação personalizada usando o evento SortCompare</span><span class="sxs-lookup"><span data-stu-id="9f63c-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="9f63c-112">O exemplo de código a seguir demonstra classificação personalizada usando um <xref:System.Windows.Forms.DataGridView.SortCompare> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9f63c-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="9f63c-113">Selecionado <xref:System.Windows.Forms.DataGridViewColumn> é classificada e, se houver valores duplicados na coluna, a coluna de ID é usada para determinar a classificação final.</span><span class="sxs-lookup"><span data-stu-id="9f63c-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="9f63c-114">Classificação personalizada usando a interface IComparer</span><span class="sxs-lookup"><span data-stu-id="9f63c-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="9f63c-115">O exemplo de código a seguir demonstra classificação personalizada usando o `Sort(IComparer)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método, que usa uma implementação da <xref:System.Collections.IComparer> interface para executar uma classificação de várias colunas.</span><span class="sxs-lookup"><span data-stu-id="9f63c-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f63c-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9f63c-116">Compiling the Code</span></span>  
 <span data-ttu-id="9f63c-117">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="9f63c-117">These examples require:</span></span>  
  
-   <span data-ttu-id="9f63c-118">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9f63c-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9f63c-119">Para obter informações sobre como compilar esses exemplos da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9f63c-119">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9f63c-120">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="9f63c-120">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f63c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f63c-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="9f63c-122">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f63c-122">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f63c-123">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f63c-123">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f63c-124">Como: Definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f63c-124">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
