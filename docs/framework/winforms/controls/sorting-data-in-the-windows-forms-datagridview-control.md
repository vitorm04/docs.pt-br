---
title: Classificando dados no controle DataGridView do Windows Forms
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012135"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d5518-102">Classificando dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5518-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="d5518-103">Por padrão, os usuários podem classificar os dados em um <xref:System.Windows.Forms.DataGridView> controle clicando no cabeçalho de uma coluna de caixa de texto (ou pressionando F3 quando uma célula de caixa de texto está focalizada no .NET Framework 4.7.2 e versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="d5518-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="d5518-104">Você pode modificar a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode> de colunas específicas para permitir aos usuários classificar por outros tipos de coluna quando fizer sentido.</span><span class="sxs-lookup"><span data-stu-id="d5518-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="d5518-105">Você também pode classificar os dados de forma programática por qualquer coluna ou por várias colunas.</span><span class="sxs-lookup"><span data-stu-id="d5518-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d5518-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d5518-106">In this section</span></span>

[<span data-ttu-id="d5518-107">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5518-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d5518-108">Descreve as opções para classificar os dados no controle.</span><span class="sxs-lookup"><span data-stu-id="d5518-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="d5518-109">Como: Definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5518-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="d5518-110">Descreve como habilitar usuários para classificar por colunas que não são classificáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="d5518-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="d5518-111">Como: Personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5518-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d5518-112">Descreve como classificar dados por meio de programação e como personalizar a classificação usando o <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> evento ou implementando o <xref:System.Collections.IComparer> interface.</span><span class="sxs-lookup"><span data-stu-id="d5518-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="d5518-113">Referência</span><span class="sxs-lookup"><span data-stu-id="d5518-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="d5518-114">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="d5518-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="d5518-115">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.Sort%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d5518-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="d5518-116">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5518-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="d5518-117">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeração.</span><span class="sxs-lookup"><span data-stu-id="d5518-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5518-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5518-118">See also</span></span>

- [<span data-ttu-id="d5518-119">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="d5518-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="d5518-120">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5518-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
