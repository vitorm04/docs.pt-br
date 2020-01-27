---
title: Usar o modelo de linha para personalizar linhas no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728390"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="544fa-102">Como usar o modelo da linha para personalizar linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="544fa-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="544fa-103">O controle de <xref:System.Windows.Forms.DataGridView> usa o modelo de linha como uma base para todas as linhas que ele adiciona ao controle por meio da vinculação de dados ou quando você chama o método <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> sem especificar uma linha existente a ser usada.</span><span class="sxs-lookup"><span data-stu-id="544fa-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="544fa-104">O modelo de linha oferece maior controle sobre a aparência e o comportamento de linhas que o <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedade fornece.</span><span class="sxs-lookup"><span data-stu-id="544fa-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="544fa-105">Com o modelo de linha, você pode definir qualquer <xref:System.Windows.Forms.DataGridViewRow> Propriedades, incluindo <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="544fa-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="544fa-106">Há algumas situações em que você deve usar o modelo de linha para obter um efeito específico.</span><span class="sxs-lookup"><span data-stu-id="544fa-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="544fa-107">Por exemplo, as informações de altura de linha não podem ser armazenadas em um <xref:System.Windows.Forms.DataGridViewCellStyle>, portanto, você deve usar um modelo de linha para alterar a altura padrão usada por todas as linhas.</span><span class="sxs-lookup"><span data-stu-id="544fa-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="544fa-108">O modelo de linha também é útil quando você cria suas próprias classes derivadas de <xref:System.Windows.Forms.DataGridViewRow> e deseja que seu tipo personalizado seja usado quando novas linhas são adicionadas ao controle.</span><span class="sxs-lookup"><span data-stu-id="544fa-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="544fa-109">O modelo de linha é usado somente quando linhas são adicionadas.</span><span class="sxs-lookup"><span data-stu-id="544fa-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="544fa-110">Você não pode alterar as linhas existentes alterando o modelo de linha.</span><span class="sxs-lookup"><span data-stu-id="544fa-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="544fa-111">Para usar o modelo de linha</span><span class="sxs-lookup"><span data-stu-id="544fa-111">To use the row template</span></span>  
  
- <span data-ttu-id="544fa-112">Defina as propriedades no objeto recuperado da propriedade <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="544fa-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="544fa-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="544fa-113">Compiling the Code</span></span>  
 <span data-ttu-id="544fa-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="544fa-114">This example requires:</span></span>  
  
- <span data-ttu-id="544fa-115">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="544fa-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="544fa-116">Referências aos assemblies <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="544fa-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544fa-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="544fa-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="544fa-118">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="544fa-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="544fa-119">Estilos de Célula no Controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="544fa-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
