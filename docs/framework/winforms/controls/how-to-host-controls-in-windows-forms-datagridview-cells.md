---
title: Controles de host em células DataGridView
description: Saiba como hospedar controles em Windows Forms células DataGridView para permitir que os usuários insiram e editem valores de várias maneiras.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619540"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="46f48-103">Como hospedar controles em células DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46f48-103">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="46f48-104">O <xref:System.Windows.Forms.DataGridView> controle fornece vários tipos de coluna, permitindo que os usuários insiram e editem valores de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="46f48-104">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="46f48-105">No entanto, se esses tipos de coluna não atenderem às suas necessidades de entrada de dados, será possível criar seus próprios tipos de coluna com células que hospedam controles de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="46f48-105">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="46f48-106">Para fazer isso, você deve definir classes que derivam de <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="46f48-106">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="46f48-107">Você também deve definir uma classe que deriva de <xref:System.Windows.Forms.Control> e implementa a <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span><span class="sxs-lookup"><span data-stu-id="46f48-107">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="46f48-108">O exemplo de código a seguir mostra como criar uma coluna de calendário.</span><span class="sxs-lookup"><span data-stu-id="46f48-108">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="46f48-109">As células desta coluna exibem datas em células de caixa de texto comuns, mas quando o usuário edita uma célula, um <xref:System.Windows.Forms.DateTimePicker> controle é exibido.</span><span class="sxs-lookup"><span data-stu-id="46f48-109">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="46f48-110">Para evitar a implementação da funcionalidade de exibição da caixa de texto novamente, a `CalendarCell` classe deriva da <xref:System.Windows.Forms.DataGridViewTextBoxCell> classe em vez de herdar a <xref:System.Windows.Forms.DataGridViewCell> classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="46f48-110">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46f48-111">Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante as operações de clonagem.</span><span class="sxs-lookup"><span data-stu-id="46f48-111">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="46f48-112">Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.</span><span class="sxs-lookup"><span data-stu-id="46f48-112">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46f48-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="46f48-113">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46f48-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="46f48-114">Compiling the Code</span></span>  
 <span data-ttu-id="46f48-115">O exemplo a seguir requer:</span><span class="sxs-lookup"><span data-stu-id="46f48-115">The following example requires:</span></span>  
  
- <span data-ttu-id="46f48-116">Referências aos assemblies System e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="46f48-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f48-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46f48-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="46f48-118">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46f48-118">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46f48-119">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="46f48-119">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="46f48-120">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46f48-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
