---
title: "Como exibir botões de opção em um MenuStrip (Windows Forms)"
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
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15f2d1492148a4b00a4b96844f546a4dc968eef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="79d27-102">Como exibir botões de opção em um MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="79d27-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="79d27-103">Botões de opção são semelhantes a caixas de seleção, exceto que os usuários podem selecionar apenas um por vez.</span><span class="sxs-lookup"><span data-stu-id="79d27-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="79d27-104">Embora, por padrão o <xref:System.Windows.Forms.ToolStripMenuItem> classe não fornecerá o comportamento do botão de opção, a classe fornece o comportamento da caixa de seleção que você pode personalizar para implementar o comportamento do botão de opção de itens de menu em um <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="79d27-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="79d27-105">Quando o <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> é de propriedade de um item de menu `true`, os usuários podem clicar no item para alternar a exibição de uma marca de seleção.</span><span class="sxs-lookup"><span data-stu-id="79d27-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="79d27-106">O <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedade indica o estado atual do item.</span><span class="sxs-lookup"><span data-stu-id="79d27-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="79d27-107">Para implementar o comportamento do botão de opção básica, você deve garantir que, quando um item é selecionado, você definir o <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedade do item selecionado anteriormente para `false`.</span><span class="sxs-lookup"><span data-stu-id="79d27-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="79d27-108">Os procedimentos a seguir descrevem como implementar isso e funcionalidades adicionais em uma classe que herda de <xref:System.Windows.Forms.ToolStripMenuItem> classe.</span><span class="sxs-lookup"><span data-stu-id="79d27-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="79d27-109">O `ToolStripRadioButtonMenuItem` classe substitui membros como <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> e <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> para fornecer o comportamento de seleção e a aparência de botões de opção.</span><span class="sxs-lookup"><span data-stu-id="79d27-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="79d27-110">Além disso, esta classe substitui o <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade para que as opções em um submenu estiver desabilitada, a menos que o item pai é selecionado.</span><span class="sxs-lookup"><span data-stu-id="79d27-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="79d27-111">Implementar o comportamento de seleção do botão de opção</span><span class="sxs-lookup"><span data-stu-id="79d27-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="79d27-112">Inicializar o <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriedade `true` para habilitar a seleção de item.</span><span class="sxs-lookup"><span data-stu-id="79d27-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="79d27-113">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> método para limpar a seleção do item selecionado anteriormente, quando um novo item é selecionado.</span><span class="sxs-lookup"><span data-stu-id="79d27-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="79d27-114">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> método para garantir que clicar em um item que já foi selecionado não limpará a seleção.</span><span class="sxs-lookup"><span data-stu-id="79d27-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="79d27-115">Modificar a aparência dos itens do botão de opção</span><span class="sxs-lookup"><span data-stu-id="79d27-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="79d27-116">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> método para substituir a marca de seleção padrão com um botão de opção usando o <xref:System.Windows.Forms.RadioButtonRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="79d27-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="79d27-117">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, e <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> métodos para controlar o estado do mouse e verifique se o <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> método pinta o estado correto do botão de opção.</span><span class="sxs-lookup"><span data-stu-id="79d27-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="79d27-118">Desabilitar as opções em um submenu quando o item pai não está selecionado</span><span class="sxs-lookup"><span data-stu-id="79d27-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="79d27-119">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade para que o item é desabilitado quando ele tem um item pai com ambos um <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> valor `true` e um <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> valor de `false`.</span><span class="sxs-lookup"><span data-stu-id="79d27-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="79d27-120">Substituir o <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> método para assinar o <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> eventos do item pai.</span><span class="sxs-lookup"><span data-stu-id="79d27-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="79d27-121">No manipulador para o item pai <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> evento, invalidar o item para atualizar a exibição com o novo estado habilitado.</span><span class="sxs-lookup"><span data-stu-id="79d27-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="79d27-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79d27-122">Example</span></span>  
 <span data-ttu-id="79d27-123">O exemplo de código a seguir fornece completo `ToolStripRadioButtonMenuItem` classe e um <xref:System.Windows.Forms.Form> classe e `Program` classe para demonstrar o comportamento do botão de opção.</span><span class="sxs-lookup"><span data-stu-id="79d27-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="79d27-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="79d27-124">Compiling the Code</span></span>  
 <span data-ttu-id="79d27-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="79d27-125">This example requires:</span></span>  
  
-   <span data-ttu-id="79d27-126">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="79d27-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d27-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79d27-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="79d27-128">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="79d27-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="79d27-129">Como implementar um ToolStripRenderer personalizado</span><span class="sxs-lookup"><span data-stu-id="79d27-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
