---
title: Funcionalidade padrão no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 1b67fa4da987778b08bad59d2e2829d0a974512a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710554"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="27a45-102">Funcionalidade padrão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27a45-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="27a45-103">Os formulários do Windows <xref:System.Windows.Forms.DataGridView> controle fornece aos usuários uma quantidade significativa de funcionalidade padrão.</span><span class="sxs-lookup"><span data-stu-id="27a45-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="27a45-104">Funcionalidade padrão</span><span class="sxs-lookup"><span data-stu-id="27a45-104">Default Functionality</span></span>  
 <span data-ttu-id="27a45-105">Por padrão, um <xref:System.Windows.Forms.DataGridView> controle:</span><span class="sxs-lookup"><span data-stu-id="27a45-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="27a45-106">Exibe automaticamente os cabeçalhos de coluna e de linha que permanecem visíveis enquanto a tabela rola verticalmente.</span><span class="sxs-lookup"><span data-stu-id="27a45-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="27a45-107">Tem um cabeçalho de linha que contém um indicador de seleção para a linha atual.</span><span class="sxs-lookup"><span data-stu-id="27a45-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="27a45-108">Tem um retângulo de seleção na primeira célula.</span><span class="sxs-lookup"><span data-stu-id="27a45-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="27a45-109">Tem colunas que podem ser redimensionadas automaticamente quando o usuário clicar duas vezes nos divisores de coluna.</span><span class="sxs-lookup"><span data-stu-id="27a45-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="27a45-110">Automaticamente dá suporte a estilos visuais no Windows XP e na família do Windows Server 2003 quando o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método é chamado a partir do aplicativo `Main` método.</span><span class="sxs-lookup"><span data-stu-id="27a45-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="27a45-111">Além disso, o conteúdo de um <xref:System.Windows.Forms.DataGridView> controle pode ser editado por padrão:</span><span class="sxs-lookup"><span data-stu-id="27a45-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="27a45-112">Se o usuário clica duas vezes ou pressiona F2 em uma célula, o controle automaticamente coloca a célula no modo de edição e atualiza o conteúdo da célula à medida que o usuário digita.</span><span class="sxs-lookup"><span data-stu-id="27a45-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="27a45-113">Se o usuário rolar até o final da grade, o usuário verá que existe uma linha para adicionar novos registros.</span><span class="sxs-lookup"><span data-stu-id="27a45-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="27a45-114">Quando o usuário clica nessa linha, uma nova linha é adicionada para o <xref:System.Windows.Forms.DataGridView> controle, com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="27a45-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="27a45-115">Quando o usuário pressiona ESC, essa nova linha desaparece.</span><span class="sxs-lookup"><span data-stu-id="27a45-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="27a45-116">Se o usuário clicar em um cabeçalho de linha, a linha inteira será selecionada.</span><span class="sxs-lookup"><span data-stu-id="27a45-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="27a45-117">Quando você associa um <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados, definindo seu <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade, o controle:</span><span class="sxs-lookup"><span data-stu-id="27a45-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="27a45-118">Usa automaticamente os nomes das colunas da fonte de dados como o texto do cabeçalho de coluna.</span><span class="sxs-lookup"><span data-stu-id="27a45-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="27a45-119">É populado com o conteúdo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="27a45-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="27a45-120"><xref:System.Windows.Forms.DataGridView> colunas são criadas automaticamente para cada coluna na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="27a45-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="27a45-121">Cria uma linha para cada linha visível na tabela.</span><span class="sxs-lookup"><span data-stu-id="27a45-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="27a45-122">Classifica automaticamente as linhas com base nos dados subjacentes quando o usuário clica em um cabeçalho de coluna.</span><span class="sxs-lookup"><span data-stu-id="27a45-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a45-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a45-123">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="27a45-124">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="27a45-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
