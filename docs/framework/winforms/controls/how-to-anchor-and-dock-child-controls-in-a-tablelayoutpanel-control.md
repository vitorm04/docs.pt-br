---
title: 'Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: a84b00e93354a9aaff074a570cee931591816161
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329915"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c1d4f-102">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1d4f-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="c1d4f-103">O <xref:System.Windows.Forms.TableLayoutPanel> controlar dá suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="c1d4f-104">Alinhar um controle filho a uma célula TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1d4f-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="c1d4f-105">Criar um <xref:System.Windows.Forms.TableLayoutPanel> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="c1d4f-106">Defina o valor da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> e <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> propriedades a serem **1**.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="c1d4f-107">Criar uma <xref:System.Windows.Forms.Button> no controlar o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="c1d4f-108">O <xref:System.Windows.Forms.Button> ocupa o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="c1d4f-109">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="c1d4f-110">O <xref:System.Windows.Forms.Button> controle se move para alinhar com a borda esquerda da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1d4f-111">Esse comportamento difere do comportamento de outras caixas de controles.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="c1d4f-112">Em outros controles de contêiner, o controle filho não se move quando a <xref:System.Windows.Forms.Control.Anchor%2A> estiver definida, e a distância entre o controle ancorado e limite do contêiner pai é determinada no momento o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="c1d4f-113">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="c1d4f-114">O <xref:System.Windows.Forms.Button> controle se move para ocupar o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="c1d4f-115">Repita a etapa 5 com um valor de `Top, Right` para mover o <xref:System.Windows.Forms.Button> controle para o canto superior direito da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="c1d4f-116">Repita com valores de `Bottom, Left` e `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="c1d4f-117">Alongar um controle filho em uma célula TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1d4f-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="c1d4f-118">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="c1d4f-119">O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar-se pela célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1d4f-120">Esse comportamento difere do comportamento de outras caixas de controles.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="c1d4f-121">Em outros controles de contêiner, o controle filho não é redimensionado quando o <xref:System.Windows.Forms.Control.Anchor%2A> estiver definida como `Left, Right` ou `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="c1d4f-122">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="c1d4f-123">O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar de cima para baixo até a parte inferior da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="c1d4f-124">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="c1d4f-125">O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="c1d4f-126">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `None`.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="c1d4f-127">O <xref:System.Windows.Forms.Button> controle é redimensionado e centralizado na célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="c1d4f-128">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="c1d4f-129">O <xref:System.Windows.Forms.Button> controle se move para alinhar com a borda esquerda da célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="c1d4f-130">O <xref:System.Windows.Forms.Button> controle mantém sua largura, mas sua altura é redimensionada para preencher a célula verticalmente.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1d4f-131">Esse é o mesmo comportamento que ocorre em outras caixas de controle.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="c1d4f-132">Altere o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="c1d4f-133">O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d4f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1d4f-134">Example</span></span>  
 <span data-ttu-id="c1d4f-135">A ilustração a seguir mostra cinco botões ancorados em cinco separado <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c1d4f-136">![Ancoragem TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="c1d4f-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="c1d4f-137">A ilustração a seguir mostra quatro botões ancorados nos cantos de quatro separado <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c1d4f-138">![Ancoragem TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="c1d4f-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="c1d4f-139">A ilustração a seguir mostra três botões alongados com ancoragem em três separado <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c1d4f-140">![Ancoragem TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="c1d4f-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="c1d4f-141">O exemplo de código a seguir demonstra todas as combinações de <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> de controle em um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1d4f-142">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c1d4f-142">Compiling the Code</span></span>  
 <span data-ttu-id="c1d4f-143">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c1d4f-143">This example requires:</span></span>  
  
-   <span data-ttu-id="c1d4f-144">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c1d4f-145">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c1d4f-145">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c1d4f-146">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c1d4f-146">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d4f-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1d4f-147">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="c1d4f-148">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1d4f-148">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
