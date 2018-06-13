---
title: Como exibir imagens em células do controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 62a29b9ade4953a1775c2a71b62e4881065f51a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531187"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="4ea6f-102">Como exibir imagens em células do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ea6f-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4ea6f-103">Uma imagem ou um gráfico é um dos valores que você pode exibir em uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="4ea6f-104">Frequentemente, esses elementos gráficos assumem a forma de foto do funcionário ou um logotipo da empresa.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="4ea6f-105">A incorporação de imagens é simple quando você exibe dados dentro de <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4ea6f-106">O <xref:System.Windows.Forms.DataGridView> controle nativamente trata qualquer formato de imagem com suporte a <xref:System.Drawing.Image> classe, bem como a OLE de formato usado por alguns bancos de dados de imagem.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="4ea6f-107">Se o <xref:System.Windows.Forms.DataGridView> fonte de dados do controle tem uma coluna de imagens, eles serão exibidos automaticamente pelo <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="4ea6f-108">O exemplo de código a seguir demonstra como extrair um ícone de um recurso inserido e convertê-lo em um bitmap para exibição em cada célula de uma coluna de imagens.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="4ea6f-109">Para obter outro exemplo que substitui os valores de célula textual por imagens correspondentes, consulte [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="4ea6f-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea6f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ea6f-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ea6f-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4ea6f-111">Compiling the Code</span></span>  
 <span data-ttu-id="4ea6f-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="4ea6f-112">This example requires:</span></span>  
  
-   <span data-ttu-id="4ea6f-113">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="4ea6f-114">Um recurso de ícone incorporado denominado `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-114">An embedded icon resource named `tree.ico`.</span></span>  
  
-   <span data-ttu-id="4ea6f-115">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="4ea6f-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea6f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ea6f-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="4ea6f-117">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ea6f-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="4ea6f-118">Como personalizar a formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ea6f-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
