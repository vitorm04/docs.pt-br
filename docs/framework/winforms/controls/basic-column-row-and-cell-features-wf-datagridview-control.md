---
title: "Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eebd0f36fbf1bf3bfc37b8fa836d318a9b8ac007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="776ba-102">Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="776ba-103">Várias funcionalidades básicas de `DataGridView` células, linhas e colunas podem ser modificadas configurando propriedades individuais.</span><span class="sxs-lookup"><span data-stu-id="776ba-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="776ba-104">Os tópicos nesta seção descrevem vários dos recursos mais usados.</span><span class="sxs-lookup"><span data-stu-id="776ba-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="776ba-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="776ba-105">In This Section</span></span>  
 [<span data-ttu-id="776ba-106">Como ocultar colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-107">Descreve como impedir que colunas específicas apareçam no controle.</span><span class="sxs-lookup"><span data-stu-id="776ba-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="776ba-108">Como ocultar cabeçalhos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-109">Descreve como impedir que os cabeçalhos das colunas apareçam no controle.</span><span class="sxs-lookup"><span data-stu-id="776ba-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="776ba-110">Como habilitar a reorganização da coluna no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-111">Descreve como habilitar usuários para reorganizar colunas no controle.</span><span class="sxs-lookup"><span data-stu-id="776ba-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="776ba-112">Como congelar colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-113">Descreve como evitar que uma ou mais colunas adjacentes rolem.</span><span class="sxs-lookup"><span data-stu-id="776ba-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="776ba-114">Como deixar colunas somente leitura no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-115">Descreve como evitar que os usuários editem colunas específicas no controle.</span><span class="sxs-lookup"><span data-stu-id="776ba-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="776ba-116">Como evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="776ba-117">Descreve como remover a linha para novos registros na parte inferior do controle para evitar que os usuários adicionem linhas.</span><span class="sxs-lookup"><span data-stu-id="776ba-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="776ba-118">Também descreve como evitar que os usuários apaguem linhas.</span><span class="sxs-lookup"><span data-stu-id="776ba-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="776ba-119">Como obter e definir a célula atual no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="776ba-120">Descreve como acessar a célula que tem foco no controle atualmente.</span><span class="sxs-lookup"><span data-stu-id="776ba-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="776ba-121">Como exibir imagens em células do controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-122">Descreve como criar uma coluna de imagem exibindo um ícone em cada célula.</span><span class="sxs-lookup"><span data-stu-id="776ba-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="776ba-123">Referência</span><span class="sxs-lookup"><span data-stu-id="776ba-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="776ba-124">Fornece documentação de referência para o controle.</span><span class="sxs-lookup"><span data-stu-id="776ba-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="776ba-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="776ba-125">Related Sections</span></span>  
 [<span data-ttu-id="776ba-126">Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="776ba-127">Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.</span><span class="sxs-lookup"><span data-stu-id="776ba-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="776ba-128">Programando com células, linhas e colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="776ba-129">Fornece tópicos que descrevem como programar com objetos de célula, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="776ba-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776ba-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="776ba-130">See Also</span></span>  
 [<span data-ttu-id="776ba-131">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="776ba-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="776ba-132">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="776ba-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
