---
title: 'Como: Adicionar um ToolStripContainer a um formulário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 9aace854a9583268ef7aac6ac1f57534cfdfe1e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515515"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="72ba1-102">Como: Adicionar um ToolStripContainer a um formulário</span><span class="sxs-lookup"><span data-stu-id="72ba1-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="72ba1-103">Você pode adicionar programaticamente uma <xref:System.Windows.Forms.ToolStripContainer> a um formulário do Windows e preenchê-lo com controles.</span><span class="sxs-lookup"><span data-stu-id="72ba1-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ba1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72ba1-104">Example</span></span>  
 <span data-ttu-id="72ba1-105">O exemplo de código a seguir demonstra como adicionar um <xref:System.Windows.Forms.ToolStripContainer> e um <xref:System.Windows.Forms.ToolStrip> a formulários do Windows, como adicionar itens para o <xref:System.Windows.Forms.ToolStrip>e como adicionar o <xref:System.Windows.Forms.ToolStrip> para o <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="72ba1-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72ba1-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="72ba1-106">Compiling the Code</span></span>  
 <span data-ttu-id="72ba1-107">Este exemplo de código requer:</span><span class="sxs-lookup"><span data-stu-id="72ba1-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="72ba1-108">Referências aos assemblies System. Drawing, System. Text e System.</span><span class="sxs-lookup"><span data-stu-id="72ba1-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="72ba1-109">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="72ba1-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="72ba1-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="72ba1-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="72ba1-111">Confira também [Como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) ou [caixa de diálogo de tarefas do ToolStripContainer](https://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="72ba1-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](https://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ba1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72ba1-112">See also</span></span>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="72ba1-113">Controle ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="72ba1-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)
- [<span data-ttu-id="72ba1-114">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="72ba1-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
