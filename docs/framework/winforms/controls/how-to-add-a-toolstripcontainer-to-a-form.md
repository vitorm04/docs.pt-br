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
ms.openlocfilehash: d70c5b8f548cf325083782d6ea185c18fd2fa003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216204"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="3f56c-102">Como: Adicionar um ToolStripContainer a um formulário</span><span class="sxs-lookup"><span data-stu-id="3f56c-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="3f56c-103">Você pode adicionar programaticamente uma <xref:System.Windows.Forms.ToolStripContainer> a um formulário do Windows e preenchê-lo com controles.</span><span class="sxs-lookup"><span data-stu-id="3f56c-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f56c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f56c-104">Example</span></span>  
 <span data-ttu-id="3f56c-105">O exemplo de código a seguir demonstra como adicionar um <xref:System.Windows.Forms.ToolStripContainer> e um <xref:System.Windows.Forms.ToolStrip> a formulários do Windows, como adicionar itens para o <xref:System.Windows.Forms.ToolStrip>e como adicionar o <xref:System.Windows.Forms.ToolStrip> para o <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> do <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="3f56c-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3f56c-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3f56c-106">Compiling the Code</span></span>  
 <span data-ttu-id="3f56c-107">Este exemplo de código requer:</span><span class="sxs-lookup"><span data-stu-id="3f56c-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="3f56c-108">Referências aos assemblies System. Drawing, System. Text e System.</span><span class="sxs-lookup"><span data-stu-id="3f56c-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3f56c-109">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3f56c-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3f56c-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="3f56c-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3f56c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f56c-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="3f56c-112">Controle ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="3f56c-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="3f56c-113">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3f56c-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
