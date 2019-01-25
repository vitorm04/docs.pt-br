---
title: 'Como: Usar a propriedade Spring de forma interativa em um StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: cfce4e75d47bcaf67610312b95093282f9d1fa91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582250"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="1a539-102">Como: Usar a propriedade Spring de forma interativa em um StatusStrip</span><span class="sxs-lookup"><span data-stu-id="1a539-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="1a539-103">Você pode usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> de controle em um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1a539-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="1a539-104">O <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade determina se o <xref:System.Windows.Forms.ToolStripStatusLabel> controle preencherá automaticamente o espaço disponível no <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1a539-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a539-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a539-105">Example</span></span>  
 <span data-ttu-id="1a539-106">O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> de controle em um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1a539-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="1a539-107">O <xref:System.Windows.Forms.ToolStripItem.Click> um recurso exclusivo do manipulador de eventos executa- ou (XOR) de operação para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1a539-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="1a539-108">Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, clique em **intermediária (Spring)** sobre o <xref:System.Windows.Forms.StatusStrip> controle para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1a539-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a539-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1a539-109">Compiling the Code</span></span>  
 <span data-ttu-id="1a539-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1a539-110">This example requires:</span></span>  
  
-   <span data-ttu-id="1a539-111">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1a539-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1a539-112">Para obter informações sobre como compilar este exemplo de linha de comando do visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1a539-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1a539-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1a539-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1a539-114">Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1a539-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a539-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a539-115">See also</span></span>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="1a539-116">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1a539-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
