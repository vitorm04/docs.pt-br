---
title: Classificando dados no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4027f3ae604f2a3ff4996855fa6dd34d4de8ea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="80747-102">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80747-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="80747-103">Por padrão, os usuários podem classificar os dados em um controle `DataGridView` clicando no cabeçalho de uma coluna de caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="80747-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="80747-104">Você pode modificar a propriedade `SortMode` de colunas específicas para permitir aos usuários classificar por outros tipos de coluna quando fizer sentido.</span><span class="sxs-lookup"><span data-stu-id="80747-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="80747-105">Você também pode classificar os dados de forma programática por qualquer coluna ou por várias colunas.</span><span class="sxs-lookup"><span data-stu-id="80747-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80747-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="80747-106">In This Section</span></span>  
 [<span data-ttu-id="80747-107">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80747-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="80747-108">Descreve as opções para classificar os dados no controle.</span><span class="sxs-lookup"><span data-stu-id="80747-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="80747-109">Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80747-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="80747-110">Descreve como habilitar usuários para classificar por colunas que não são classificáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="80747-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="80747-111">Como personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80747-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="80747-112">Descreve como classificar dados por meio de programação e como personalizar a classificação usando o <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> evento ou implementando o <xref:System.Collections.IComparer> interface.</span><span class="sxs-lookup"><span data-stu-id="80747-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="80747-113">Referência</span><span class="sxs-lookup"><span data-stu-id="80747-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="80747-114">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="80747-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="80747-115">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.Sort%2A> método.</span><span class="sxs-lookup"><span data-stu-id="80747-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="80747-116">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="80747-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="80747-117">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeração.</span><span class="sxs-lookup"><span data-stu-id="80747-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80747-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80747-118">See Also</span></span>  
 [<span data-ttu-id="80747-119">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="80747-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="80747-120">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80747-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
