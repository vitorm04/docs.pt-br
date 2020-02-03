---
title: Controles de host em células DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736533"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="00b17-102">Como hospedar controles em células DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00b17-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="00b17-103">O controle de <xref:System.Windows.Forms.DataGridView> fornece vários tipos de coluna, permitindo que os usuários insiram e editem valores de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="00b17-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="00b17-104">No entanto, se esses tipos de coluna não atenderem às suas necessidades de entrada de dados, será possível criar seus próprios tipos de coluna com células que hospedam controles de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="00b17-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="00b17-105">Para fazer isso, você deve definir classes que derivam de <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="00b17-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="00b17-106">Você também deve definir uma classe que deriva de <xref:System.Windows.Forms.Control> e implementa a interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="00b17-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="00b17-107">O exemplo de código a seguir mostra como criar uma coluna de calendário.</span><span class="sxs-lookup"><span data-stu-id="00b17-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="00b17-108">As células desta coluna exibem datas em células de caixa de texto comuns, mas quando o usuário edita uma célula, um controle de <xref:System.Windows.Forms.DateTimePicker> é exibido.</span><span class="sxs-lookup"><span data-stu-id="00b17-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="00b17-109">Para evitar a implementação da funcionalidade de exibição da caixa de texto novamente, a classe `CalendarCell` deriva da classe <xref:System.Windows.Forms.DataGridViewTextBoxCell> em vez de herdar a classe <xref:System.Windows.Forms.DataGridViewCell> diretamente.</span><span class="sxs-lookup"><span data-stu-id="00b17-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00b17-110">Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o método `Clone` para copiar as novas propriedades durante as operações de clonagem.</span><span class="sxs-lookup"><span data-stu-id="00b17-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="00b17-111">Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.</span><span class="sxs-lookup"><span data-stu-id="00b17-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b17-112">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="00b17-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00b17-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="00b17-113">Compiling the Code</span></span>  
 <span data-ttu-id="00b17-114">O exemplo a seguir requer:</span><span class="sxs-lookup"><span data-stu-id="00b17-114">The following example requires:</span></span>  
  
- <span data-ttu-id="00b17-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="00b17-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b17-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00b17-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="00b17-117">Personalizando o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00b17-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="00b17-118">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="00b17-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="00b17-119">Tipos de coluna no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00b17-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
