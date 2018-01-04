---
title: Entrada de dados no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399520738c53e149e7a5539a62a5d4599e26a8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a396d-102">Entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a396d-103">O controle `DataGridView` oferece vários recursos que permitem a você alterar como os usuários adicionam ou modificam dados no controle.</span><span class="sxs-lookup"><span data-stu-id="a396d-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="a396d-104">Por exemplo, é possível tornar a entrada de dados mais eficiente fornecendo os valores padrão para novas linhas e alertando usuários quando ocorrem erros.</span><span class="sxs-lookup"><span data-stu-id="a396d-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a396d-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a396d-105">In This Section</span></span>  
 [<span data-ttu-id="a396d-106">Como especificar o modo de edição do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a396d-107">Descreve como alterar a maneira como os usuários iniciam a edição de células.</span><span class="sxs-lookup"><span data-stu-id="a396d-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="a396d-108">Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="a396d-109">Descreve como preencher previamente a linha para novos registros para economizar tempo de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="a396d-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="a396d-110">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a396d-111">Descreve a linha para novos registros detalhadamente, incluindo informações nas ocultá-lo, personalizar sua aparência, e como ele está relacionado a <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="a396d-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="a396d-112">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a396d-113">Descreve como validar a entrada do usuário para evitar erros de formatação de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="a396d-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="a396d-114">Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="a396d-115">Descreve como manipular erros de entrada de dados que se originam da fonte de dados quando o usuário tentar confirmar um novo valor.</span><span class="sxs-lookup"><span data-stu-id="a396d-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a396d-116">Referência</span><span class="sxs-lookup"><span data-stu-id="a396d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a396d-117">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="a396d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a396d-118">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.EditMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a396d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="a396d-119">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> evento.</span><span class="sxs-lookup"><span data-stu-id="a396d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="a396d-120">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.DataError> evento.</span><span class="sxs-lookup"><span data-stu-id="a396d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="a396d-121">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.CellValidating> evento.</span><span class="sxs-lookup"><span data-stu-id="a396d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a396d-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a396d-122">Related Sections</span></span>  
 [<span data-ttu-id="a396d-123">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a396d-124">Fornece tópicos que descrevem como preencher o controle com os dados manualmente ou de uma fonte de dados externa.</span><span class="sxs-lookup"><span data-stu-id="a396d-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a396d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a396d-125">See Also</span></span>  
 [<span data-ttu-id="a396d-126">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="a396d-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="a396d-127">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a396d-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
