---
title: 'Como: Definir estilos de linha alternados para o controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962270"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="f76e4-102">Como: Definir estilos de linha alternados para o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f76e4-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f76e4-103">Dados tabulares geralmente são apresentados aos usuários em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente.</span><span class="sxs-lookup"><span data-stu-id="f76e4-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="f76e4-104">Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.</span><span class="sxs-lookup"><span data-stu-id="f76e4-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="f76e4-105">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para alternar linhas.</span><span class="sxs-lookup"><span data-stu-id="f76e4-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="f76e4-106">Isso permite usar as características de estilo como cor e fonte de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="f76e4-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="f76e4-107">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f76e4-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f76e4-108">Consulte [também como: Defina os estilos de linha alternados para o controle Windows Forms DataGridView](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)usando o designer.</span><span class="sxs-lookup"><span data-stu-id="f76e4-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="f76e4-109">Para definir estilos de linha alternada de forma programática</span><span class="sxs-lookup"><span data-stu-id="f76e4-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="f76e4-110">Defina <xref:System.Windows.Forms.DataGridViewCellStyle> as propriedades dos objetos retornados <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> pelas propriedades e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> do <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f76e4-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="f76e4-111">Os estilos especificados usando as <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedades <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> e substituem os estilos especificados na coluna e <xref:System.Windows.Forms.DataGridView> no nível, mas são substituídos pelos estilos definidos no nível de linha e célula individuais.</span><span class="sxs-lookup"><span data-stu-id="f76e4-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="f76e4-112">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f76e4-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f76e4-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f76e4-113">Compiling the Code</span></span>  
 <span data-ttu-id="f76e4-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f76e4-114">This example requires:</span></span>  
  
- <span data-ttu-id="f76e4-115">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f76e4-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f76e4-116">Referências aos <xref:System?displayProperty=nameWithType>assemblies, <xref:System.Drawing?displayProperty=nameWithType>e. <xref:System.Windows.Forms?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f76e4-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f76e4-117">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f76e4-117">Robust Programming</span></span>  
 <span data-ttu-id="f76e4-118">Para obter a escalabilidade máxima, <xref:System.Windows.Forms.DataGridViewCellStyle> você deve compartilhar objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente.</span><span class="sxs-lookup"><span data-stu-id="f76e4-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="f76e4-119">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f76e4-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76e4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76e4-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="f76e4-121">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f76e4-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f76e4-122">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f76e4-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f76e4-123">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f76e4-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f76e4-124">Como: Definir estilos de fonte e cor no controle Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f76e4-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
