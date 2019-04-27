---
title: Seleção e uso da Área de Transferência com o controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 1836fbc1887082ca685c49bef2bc42bdb167578f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902242"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="374f6-102">Seleção e uso da Área de Transferência com o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="374f6-103">O controle `DataGridView` oferece uma variedade de opções para configurar como os usuários podem selecionar células, linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="374f6-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="374f6-104">Por exemplo, você pode habilitar uma ou várias seleções, seleção de todas as linhas ou colunas quando os usuários clicam em células ou de todas as linhas ou colunas somente quando os usuários clicam em seus cabeçalhos, o que permite a seleção da célula também.</span><span class="sxs-lookup"><span data-stu-id="374f6-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="374f6-105">Se você quiser fornecer sua própria interface do usuário para seleção, desabilite a seleção comum e gerencie todas as seleções de forma programática.</span><span class="sxs-lookup"><span data-stu-id="374f6-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="374f6-106">Além disso, você pode permitir que os usuários copiem os valores selecionados para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="374f6-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="374f6-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="374f6-107">In This Section</span></span>  
 [<span data-ttu-id="374f6-108">Modos de seleção no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="374f6-109">Descreve as opções para seleção do usuário e programática no controle.</span><span class="sxs-lookup"><span data-stu-id="374f6-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="374f6-110">Como: Definir o modo de seleção do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="374f6-111">Descreve como configurar o controle para seleção única linha quando um usuário clica em uma célula.</span><span class="sxs-lookup"><span data-stu-id="374f6-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="374f6-112">Como: Obter as células selecionadas, linhas e colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="374f6-113">Descreve como trabalhar com as coleções selecionadas de célula, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="374f6-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="374f6-114">Como: Permitir que os usuários para copiarem várias células na área de transferência do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="374f6-115">Descreve como habilitar o suporte à área de transferência no controle.</span><span class="sxs-lookup"><span data-stu-id="374f6-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="374f6-116">Referência</span><span class="sxs-lookup"><span data-stu-id="374f6-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="374f6-117">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="374f6-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="374f6-118">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="374f6-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="374f6-119">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="374f6-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="374f6-120">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="374f6-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="374f6-121">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="374f6-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="374f6-122">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="374f6-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374f6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="374f6-123">See also</span></span>

- [<span data-ttu-id="374f6-124">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="374f6-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="374f6-125">Tratamento de teclado e mouse padrão no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="374f6-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
