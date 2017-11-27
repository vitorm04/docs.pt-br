---
title: Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms
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
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a31e8eb02949c0f6db487e3cd1a6976f2ed37222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="f3dd2-102">Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f3dd2-103">Dados tabulares geralmente são apresentados aos usuários em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="f3dd2-104">Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="f3dd2-105">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completo de linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="f3dd2-106">Isso permite usar as características de estilo como cor e fonte de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="f3dd2-107">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f3dd2-108">Veja também [Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="f3dd2-109">Para definir estilos de linha alternada de forma programática</span><span class="sxs-lookup"><span data-stu-id="f3dd2-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="f3dd2-110">Definir as propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> objetos retornados pelo <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedades da <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f3dd2-111">Os estilos especificados usando o <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedades substituem os estilos especificados na coluna e <xref:System.Windows.Forms.DataGridView> nível, mas são substituídas pelos estilos definido no nível de linha e célula individual.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="f3dd2-112">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3dd2-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f3dd2-113">Compiling the Code</span></span>  
 <span data-ttu-id="f3dd2-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f3dd2-114">This example requires:</span></span>  
  
-   <span data-ttu-id="f3dd2-115">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="f3dd2-116">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f3dd2-117">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f3dd2-117">Robust Programming</span></span>  
 <span data-ttu-id="f3dd2-118">Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="f3dd2-119">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dd2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3dd2-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="f3dd2-121">Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f3dd2-122">Estilos de Célula no Controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f3dd2-123">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f3dd2-124">Como definir estilos de fonte e cor no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
