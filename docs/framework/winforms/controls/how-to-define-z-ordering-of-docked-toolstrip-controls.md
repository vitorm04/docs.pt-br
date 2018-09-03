---
title: Como definir a organização Z de controles ToolStrip encaixados
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
ms.openlocfilehash: 34d600454a7fa63c7ba59bebded6365cd5401cb4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466305"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="0c1dc-102">Como definir a organização Z de controles ToolStrip encaixados</span><span class="sxs-lookup"><span data-stu-id="0c1dc-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="0c1dc-103">A posição um <xref:System.Windows.Forms.ToolStrip> controle corretamente com o encaixe, você deve posicionar o controle corretamente na ordem z do formulário.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c1dc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c1dc-104">Example</span></span>  
 <span data-ttu-id="0c1dc-105">O exemplo de código a seguir demonstra como organizar um <xref:System.Windows.Forms.ToolStrip> controle e um encaixado <xref:System.Windows.Forms.MenuStrip> controle especificando a ordem z.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="0c1dc-106">A ordem z é determinada pela ordem na qual o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="0c1dc-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="0c1dc-107">controles são adicionados ao formulário <xref:System.Windows.Forms.Control.Controls%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="0c1dc-108">Inverter a ordem dessas chamadas para o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> o efeito no layout de exibição e o método.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c1dc-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0c1dc-109">Compiling the Code</span></span>  
 <span data-ttu-id="0c1dc-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0c1dc-110">This example requires:</span></span>  
  
-   <span data-ttu-id="0c1dc-111">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0c1dc-112">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0c1dc-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0c1dc-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="0c1dc-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0c1dc-114">Também sar [como: compilar e executar um Windows Forms código de exemplo completo usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0c1dc-114">Also se [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1dc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c1dc-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>  
 <xref:System.Windows.Forms.Control.Controls%2A>  
 <xref:System.Windows.Forms.Control.Dock%2A>  
 [<span data-ttu-id="0c1dc-116">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0c1dc-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
