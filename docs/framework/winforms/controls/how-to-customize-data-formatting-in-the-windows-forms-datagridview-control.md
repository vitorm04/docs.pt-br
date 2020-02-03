---
title: Personalizar a formatação de dados no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746781"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f6161-102">Como personalizar a formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6161-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f6161-103">O exemplo de código a seguir demonstra como implementar um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> que altera como as células são exibidas, dependendo de suas colunas e valores.</span><span class="sxs-lookup"><span data-stu-id="f6161-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="f6161-104">As células na coluna `Balance` que contêm números negativos recebem um plano de fundo vermelho.</span><span class="sxs-lookup"><span data-stu-id="f6161-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="f6161-105">Você também pode formatar essas células como moeda para exibir parênteses em valores negativos.</span><span class="sxs-lookup"><span data-stu-id="f6161-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="f6161-106">Para obter mais informações, consulte [Como formatar dados no controle DataGridView do Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f6161-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f6161-107">As células na coluna `Priority` exibem imagens no lugar de valores de células textuais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="f6161-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="f6161-108">A propriedade <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> da <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> é usada para obter o valor da célula textual e para definir o valor de exibição da imagem correspondente.</span><span class="sxs-lookup"><span data-stu-id="f6161-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6161-109">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f6161-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6161-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="f6161-110">Compiling the Code</span></span>  
 <span data-ttu-id="f6161-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f6161-111">This example requires:</span></span>  
  
- <span data-ttu-id="f6161-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f6161-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="f6161-113"><xref:System.Drawing.Bitmap> imagens nomeadas `highPri.bmp`, `mediumPri.bmp`e `lowPri.bmp` que residem no mesmo diretório que o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="f6161-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6161-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6161-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="f6161-115">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6161-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f6161-116">Como formatar dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6161-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f6161-117">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6161-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f6161-118">Formatação de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6161-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
