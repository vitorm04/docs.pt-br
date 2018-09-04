---
title: Como habilitar margens de verificação e de imagem em controles ContextMenuStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ShowCheckMargin property [Windows Forms]
- ShowImageMargin property [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: eb584e71-59da-4012-aaca-dbe1c7c7a156
ms.openlocfilehash: f7128c8ba6e2a221e359cd761cdc4c3521bb2b99
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535281"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a><span data-ttu-id="5a8dc-102">Como habilitar margens de verificação e de imagem em controles ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="5a8dc-102">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>
<span data-ttu-id="5a8dc-103">Você pode personalizar o <xref:System.Windows.Forms.ToolStripMenuItem> objetos no seu <xref:System.Windows.Forms.MenuStrip> controle com marcas de seleção e imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-103">You can customize the <xref:System.Windows.Forms.ToolStripMenuItem> objects in your <xref:System.Windows.Forms.MenuStrip> control with check marks and custom images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a8dc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a8dc-104">Example</span></span>  
 <span data-ttu-id="5a8dc-105">O exemplo de código a seguir demonstra como criar itens de menu que têm marcas de seleção e imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-105">The following code example demonstrates how to create menu items that have check marks and custom images.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 <span data-ttu-id="5a8dc-106">Defina as <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> propriedades para especificar quando as marcas de seleção e imagens personalizadas aparecem em seus itens de menu.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-106">Set the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> properties to specify when check marks and custom images appear in your menu items.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a8dc-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5a8dc-107">Compiling the Code</span></span>  
 <span data-ttu-id="5a8dc-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5a8dc-108">This example requires:</span></span>  
  
-   <span data-ttu-id="5a8dc-109">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-109">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5a8dc-110">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5a8dc-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5a8dc-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="5a8dc-112">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5a8dc-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8dc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a8dc-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDownMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="5a8dc-114">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5a8dc-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
