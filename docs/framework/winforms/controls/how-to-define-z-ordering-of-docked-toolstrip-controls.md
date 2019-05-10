---
title: 'Como: Definir a organização Z de controles ToolStrip encaixados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: b7643c9599ceeba08cbe9f5580739043f6d89edc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666333"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="e89d1-102">Como: Definir a organização Z de controles ToolStrip encaixados</span><span class="sxs-lookup"><span data-stu-id="e89d1-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="e89d1-103">A posição um <xref:System.Windows.Forms.ToolStrip> controle corretamente com o encaixe, você deve posicionar o controle corretamente na ordem z do formulário.</span><span class="sxs-lookup"><span data-stu-id="e89d1-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e89d1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e89d1-104">Example</span></span>  
 <span data-ttu-id="e89d1-105">O exemplo de código a seguir demonstra como organizar um <xref:System.Windows.Forms.ToolStrip> controle e um encaixado <xref:System.Windows.Forms.MenuStrip> controle especificando a ordem z.</span><span class="sxs-lookup"><span data-stu-id="e89d1-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="e89d1-106">A ordem z é determinada pela ordem na qual o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="e89d1-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="e89d1-107">controles são adicionados ao formulário <xref:System.Windows.Forms.Control.Controls%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="e89d1-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="e89d1-108">Inverter a ordem dessas chamadas para o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> o efeito no layout de exibição e o método.</span><span class="sxs-lookup"><span data-stu-id="e89d1-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e89d1-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e89d1-109">Compiling the Code</span></span>  
 <span data-ttu-id="e89d1-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e89d1-110">This example requires:</span></span>  
  
- <span data-ttu-id="e89d1-111">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e89d1-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e89d1-112">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e89d1-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e89d1-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e89d1-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89d1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e89d1-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="e89d1-115">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e89d1-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
