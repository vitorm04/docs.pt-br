---
title: 'Como: Desabilitar botões em uma coluna de botão no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 7d6223e4d75524044e701ea4cf34dcc7487ccd25
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591790"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c295d-102">Como: Desabilitar botões em uma coluna de botão no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c295d-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c295d-103">O <xref:System.Windows.Forms.DataGridView> controle inclui o <xref:System.Windows.Forms.DataGridViewButtonCell> classe para exibir células com uma interface do usuário (IU) como um botão.</span><span class="sxs-lookup"><span data-stu-id="c295d-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="c295d-104">No entanto, <xref:System.Windows.Forms.DataGridViewButtonCell> não fornece uma maneira de desabilitar a aparência do botão exibido pela célula.</span><span class="sxs-lookup"><span data-stu-id="c295d-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="c295d-105">O exemplo de código a seguir demonstra como personalizar o <xref:System.Windows.Forms.DataGridViewButtonCell> classe para exibir botões que podem parecer desabilitados.</span><span class="sxs-lookup"><span data-stu-id="c295d-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="c295d-106">O exemplo define um novo tipo de célula `DataGridViewDisableButtonCell`, que deriva de <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="c295d-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="c295d-107">Esse tipo de célula fornece uma nova propriedade `Enabled` que pode ser definida como `false` para desenhar um botão desabilitado na célula.</span><span class="sxs-lookup"><span data-stu-id="c295d-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="c295d-108">O exemplo também define um novo tipo de coluna, `DataGridViewDisableButtonColumn`, que exibe objetos `DataGridViewDisableButtonCell`.</span><span class="sxs-lookup"><span data-stu-id="c295d-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="c295d-109">Para demonstrar essa nova célula e a coluna de tipo, o valor atual de cada <xref:System.Windows.Forms.DataGridViewCheckBoxCell> no pai <xref:System.Windows.Forms.DataGridView> determina se o `Enabled` propriedade o `DataGridViewDisableButtonCell` na mesma linha é `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c295d-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c295d-110">Quando você deriva <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adicionar novas propriedades à classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante operações de clonagem.</span><span class="sxs-lookup"><span data-stu-id="c295d-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="c295d-111">Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.</span><span class="sxs-lookup"><span data-stu-id="c295d-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c295d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c295d-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c295d-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c295d-113">Compiling the Code</span></span>  
 <span data-ttu-id="c295d-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c295d-114">This example requires:</span></span>  
  
- <span data-ttu-id="c295d-115">Referências aos assemblies System, System.Drawing, System.Windows.Forms e System.Windows.Forms.VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="c295d-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c295d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c295d-116">See also</span></span>

- [<span data-ttu-id="c295d-117">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c295d-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c295d-118">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c295d-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="c295d-119">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c295d-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
