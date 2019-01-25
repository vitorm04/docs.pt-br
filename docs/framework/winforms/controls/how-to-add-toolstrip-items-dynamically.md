---
title: 'Como: Adicionar itens ToolStrip dinamicamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 5f2d7c2ae604100b7fc599e11acc19cbad37ff87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504061"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="b7c3d-102">Como: Adicionar itens ToolStrip dinamicamente</span><span class="sxs-lookup"><span data-stu-id="b7c3d-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="b7c3d-103">Você pode preencher a coleção de itens de menu de dinamicamente um <xref:System.Windows.Forms.ToolStrip> controlar quando o menu é aberto.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7c3d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7c3d-104">Example</span></span>  
 <span data-ttu-id="b7c3d-105">O exemplo de código a seguir demonstra como adicionar dinamicamente os itens para um <xref:System.Windows.Forms.ContextMenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="b7c3d-106">O exemplo também mostra como reutilizar o mesmo <xref:System.Windows.Forms.ContextMenuStrip> para três diferentes controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="b7c3d-107">No exemplo, um <xref:System.Windows.Forms.ToolStripDropDown.Opening> manipulador de eventos preenche a coleção de itens de menu.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="b7c3d-108">O <xref:System.Windows.Forms.ToolStripDropDown.Opening> examina de manipulador de eventos do <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> propriedades e adiciona um <xref:System.Windows.Forms.ToolStripItem> que descreve o controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7c3d-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b7c3d-109">Compiling the Code</span></span>  
 <span data-ttu-id="b7c3d-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b7c3d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="b7c3d-111">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b7c3d-112">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b7c3d-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b7c3d-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="b7c3d-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c3d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7c3d-114">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="b7c3d-115">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b7c3d-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
