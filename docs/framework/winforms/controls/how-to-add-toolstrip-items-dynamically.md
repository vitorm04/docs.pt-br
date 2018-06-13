---
title: Como adicionar itens ToolStrip de forma dinâmica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9db50c1966d7a6c2baa344857b03e568dbe2a2ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526308"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="3ed4f-102">Como adicionar itens ToolStrip de forma dinâmica</span><span class="sxs-lookup"><span data-stu-id="3ed4f-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="3ed4f-103">Você pode preencher a coleção de itens de menu do dinamicamente um <xref:System.Windows.Forms.ToolStrip> quando abre o menu de controle.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed4f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ed4f-104">Example</span></span>  
 <span data-ttu-id="3ed4f-105">O exemplo de código a seguir demonstra como adicionar dinamicamente os itens a um <xref:System.Windows.Forms.ContextMenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="3ed4f-106">O exemplo também mostra como reutilizar o mesmo <xref:System.Windows.Forms.ContextMenuStrip> para três diferentes controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="3ed4f-107">No exemplo, um <xref:System.Windows.Forms.ToolStripDropDown.Opening> manipulador de eventos preenche a coleção de itens de menu.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="3ed4f-108">O <xref:System.Windows.Forms.ToolStripDropDown.Opening> examina o manipulador de eventos de <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> propriedades e adiciona um <xref:System.Windows.Forms.ToolStripItem> que descreve o controle de origem.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ed4f-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3ed4f-109">Compiling the Code</span></span>  
 <span data-ttu-id="3ed4f-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="3ed4f-110">This example requires:</span></span>  
  
-   <span data-ttu-id="3ed4f-111">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3ed4f-112">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3ed4f-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3ed4f-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="3ed4f-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed4f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ed4f-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 [<span data-ttu-id="3ed4f-115">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3ed4f-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
