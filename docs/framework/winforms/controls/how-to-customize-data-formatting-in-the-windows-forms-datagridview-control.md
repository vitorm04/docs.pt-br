---
title: 'Como: Personalizar a formatação de dados no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: 948e9bf485b42b445491a4da9f8de7ae7974075c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592828"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b30f7-102">Como: Personalizar a formatação de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b30f7-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b30f7-103">O exemplo de código a seguir demonstra como implementar um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento que altera como as células são exibidas, dependendo de suas colunas e valores.</span><span class="sxs-lookup"><span data-stu-id="b30f7-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="b30f7-104">Células no `Balance` coluna que contêm números negativos são fornecidos a um plano de fundo vermelho.</span><span class="sxs-lookup"><span data-stu-id="b30f7-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="b30f7-105">Você também pode formatar essas células como moeda para exibir valores negativos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b30f7-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="b30f7-106">Para obter mais informações, confira [Como: Formatar dados no Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b30f7-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="b30f7-107">Células no `Priority` valores de célula de imagens de exibição de coluna no lugar de correspondente textual.</span><span class="sxs-lookup"><span data-stu-id="b30f7-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="b30f7-108">O <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriedade do <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> é usado para obter o valor de célula textual e para definir o valor de exibição de imagem correspondente.</span><span class="sxs-lookup"><span data-stu-id="b30f7-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b30f7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b30f7-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b30f7-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b30f7-110">Compiling the Code</span></span>  
 <span data-ttu-id="b30f7-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b30f7-111">This example requires:</span></span>  
  
- <span data-ttu-id="b30f7-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b30f7-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="b30f7-113"><xref:System.Drawing.Bitmap> imagens denominadas `highPri.bmp`, `mediumPri.bmp`, e `lowPri.bmp` que residem no mesmo diretório que o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="b30f7-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30f7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b30f7-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="b30f7-115">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b30f7-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b30f7-116">Como: Formatar dados no Windows Forms DataGridView Control</span><span class="sxs-lookup"><span data-stu-id="b30f7-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b30f7-117">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b30f7-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b30f7-118">Formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b30f7-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
