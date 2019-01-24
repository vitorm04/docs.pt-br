---
title: Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: af8dcaf8b6d32f03c2f2f46312d1290a99381c43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611485"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d5edd-102">Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d5edd-103">Várias funcionalidades básicas de `DataGridView` células, linhas e colunas podem ser modificadas configurando propriedades individuais.</span><span class="sxs-lookup"><span data-stu-id="d5edd-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="d5edd-104">Os tópicos nesta seção descrevem vários dos recursos mais usados.</span><span class="sxs-lookup"><span data-stu-id="d5edd-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5edd-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d5edd-105">In This Section</span></span>  
 [<span data-ttu-id="d5edd-106">Como: Ocultar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-107">Descreve como impedir que colunas específicas apareçam no controle.</span><span class="sxs-lookup"><span data-stu-id="d5edd-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="d5edd-108">Como: Ocultar cabeçalhos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-109">Descreve como impedir que os cabeçalhos das colunas apareçam no controle.</span><span class="sxs-lookup"><span data-stu-id="d5edd-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="d5edd-110">Como: Habilitar a reorganização de colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-111">Descreve como habilitar usuários para reorganizar colunas no controle.</span><span class="sxs-lookup"><span data-stu-id="d5edd-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="d5edd-112">Como: Congelar colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-113">Descreve como evitar que uma ou mais colunas adjacentes rolem.</span><span class="sxs-lookup"><span data-stu-id="d5edd-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="d5edd-114">Como: Tornar colunas somente leitura no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-115">Descreve como evitar que os usuários editem colunas específicas no controle.</span><span class="sxs-lookup"><span data-stu-id="d5edd-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="d5edd-116">Como: Evitar a adição de linha e exclusão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="d5edd-117">Descreve como remover a linha para novos registros na parte inferior do controle para evitar que os usuários adicionem linhas.</span><span class="sxs-lookup"><span data-stu-id="d5edd-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="d5edd-118">Também descreve como evitar que os usuários apaguem linhas.</span><span class="sxs-lookup"><span data-stu-id="d5edd-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="d5edd-119">Como: Obter e definir a célula atual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="d5edd-120">Descreve como acessar a célula que tem foco no controle atualmente.</span><span class="sxs-lookup"><span data-stu-id="d5edd-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="d5edd-121">Como: Exibir imagens em células do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-122">Descreve como criar uma coluna de imagem exibindo um ícone em cada célula.</span><span class="sxs-lookup"><span data-stu-id="d5edd-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d5edd-123">Referência</span><span class="sxs-lookup"><span data-stu-id="d5edd-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="d5edd-124">Fornece documentação de referência para o controle.</span><span class="sxs-lookup"><span data-stu-id="d5edd-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5edd-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d5edd-125">Related Sections</span></span>  
 [<span data-ttu-id="d5edd-126">Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d5edd-127">Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.</span><span class="sxs-lookup"><span data-stu-id="d5edd-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="d5edd-128">Programando com células, linhas e colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="d5edd-129">Fornece tópicos que descrevem como programar com objetos de célula, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="d5edd-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5edd-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5edd-130">See also</span></span>
- [<span data-ttu-id="d5edd-131">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="d5edd-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="d5edd-132">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5edd-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
