---
title: Como ancorar e encaixar controles filho em um controle TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15a725f7a5a4b61f826756c4c3f0d2a20c8a5011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="b653c-102">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b653c-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="b653c-103">O <xref:System.Windows.Forms.TableLayoutPanel> controle oferece suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filhos.</span><span class="sxs-lookup"><span data-stu-id="b653c-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="b653c-104">Alinhar um controle filho a uma célula TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b653c-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="b653c-105">Criar um <xref:System.Windows.Forms.TableLayoutPanel> controle do formulário.</span><span class="sxs-lookup"><span data-stu-id="b653c-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="b653c-106">Defina o valor da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> e <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> propriedades **1**.</span><span class="sxs-lookup"><span data-stu-id="b653c-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="b653c-107">Criar um <xref:System.Windows.Forms.Button> controlar o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="b653c-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b653c-108">O <xref:System.Windows.Forms.Button> ocupe o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="b653c-109">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left`.</span><span class="sxs-lookup"><span data-stu-id="b653c-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="b653c-110">O <xref:System.Windows.Forms.Button> move o controle para alinhar com a borda esquerda da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b653c-111">Esse comportamento difere do comportamento de outras caixas de controles.</span><span class="sxs-lookup"><span data-stu-id="b653c-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="b653c-112">Em outros controles de contêiner, o controle filho não move quando o <xref:System.Windows.Forms.Control.Anchor%2A> está definida e a distância entre o controle ancorado e limites do contêiner pai é fixo no momento em que o <xref:System.Windows.Forms.Control.Anchor%2A> está definida.</span><span class="sxs-lookup"><span data-stu-id="b653c-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="b653c-113">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="b653c-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="b653c-114">O <xref:System.Windows.Forms.Button> move o controle para ocupar o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="b653c-115">Repita a etapa 5 com um valor de `Top, Right` para mover o <xref:System.Windows.Forms.Button> controle para o canto superior direito da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="b653c-116">Repita com valores de `Bottom, Left` e `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="b653c-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="b653c-117">Alongar um controle filho em uma célula TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b653c-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="b653c-118">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="b653c-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="b653c-119">O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar para a célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b653c-120">Esse comportamento difere do comportamento de outras caixas de controles.</span><span class="sxs-lookup"><span data-stu-id="b653c-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="b653c-121">Em outros controles de contêiner, o controle filho não é redimensionado quando o <xref:System.Windows.Forms.Control.Anchor%2A> está definida como `Left, Right` ou `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="b653c-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="b653c-122">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="b653c-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="b653c-123">O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar da parte superior para a parte inferior da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="b653c-124">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="b653c-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="b653c-125">O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="b653c-126">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `None`.</span><span class="sxs-lookup"><span data-stu-id="b653c-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="b653c-127">O <xref:System.Windows.Forms.Button> controle é redimensionado e centralizado na célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="b653c-128">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="b653c-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="b653c-129">O <xref:System.Windows.Forms.Button> move o controle para alinhar com a borda esquerda da célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="b653c-130">O <xref:System.Windows.Forms.Button> controle retém sua largura, mas sua altura é redimensionada para preencher a célula verticalmente.</span><span class="sxs-lookup"><span data-stu-id="b653c-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b653c-131">Esse é o mesmo comportamento que ocorre em outras caixas de controle.</span><span class="sxs-lookup"><span data-stu-id="b653c-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="b653c-132">Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="b653c-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="b653c-133">O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="b653c-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b653c-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b653c-134">Example</span></span>  
 <span data-ttu-id="b653c-135">A ilustração a seguir mostra cinco botões ancorado em cinco separada <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="b653c-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="b653c-136">![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="b653c-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="b653c-137">A ilustração a seguir mostra quatro botões ancorado nos cantos do separado quatro <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="b653c-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="b653c-138">![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="b653c-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="b653c-139">A ilustração a seguir mostra três botões ampliados por ancoragem em três separada <xref:System.Windows.Forms.TableLayoutPanel> células.</span><span class="sxs-lookup"><span data-stu-id="b653c-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="b653c-140">![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="b653c-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="b653c-141">O exemplo de código a seguir demonstra todas as combinações de <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> controlar um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="b653c-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b653c-142">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b653c-142">Compiling the Code</span></span>  
 <span data-ttu-id="b653c-143">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b653c-143">This example requires:</span></span>  
  
-   <span data-ttu-id="b653c-144">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b653c-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b653c-145">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="b653c-145">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b653c-146">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="b653c-146">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b653c-147">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="b653c-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b653c-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b653c-148">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="b653c-149">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b653c-149">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
