---
title: 'Como: Criar um formulário MDI com controles ToolStripPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 55c2294496800fb8692d3c8215c1c13f7dac9b01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746937"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="936d4-102">Como: Criar um formulário MDI com controles ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="936d4-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="936d4-103">Você pode criar um formulário de MDI (interface MDI) de vários documentos que tem <xref:System.Windows.Forms.ToolStrip> controles de delimitação de quadros nos quatro lados.</span><span class="sxs-lookup"><span data-stu-id="936d4-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="936d4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="936d4-104">Example</span></span>  
 <span data-ttu-id="936d4-105">O exemplo de código a seguir demonstra como usar encaixado <xref:System.Windows.Forms.ToolStripPanel> controles a uma janela MDI com quatro de quadro <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="936d4-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="936d4-106">No exemplo, o <xref:System.Windows.Forms.ToolStripPanel.Join%2A> método anexa o <xref:System.Windows.Forms.ToolStrip> controles para os respectivos <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="936d4-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="936d4-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="936d4-107">Compiling the Code</span></span>  
 <span data-ttu-id="936d4-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="936d4-108">This example requires:</span></span>  
  
- <span data-ttu-id="936d4-109">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="936d4-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="936d4-110">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="936d4-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="936d4-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="936d4-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="936d4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="936d4-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="936d4-113">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="936d4-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
