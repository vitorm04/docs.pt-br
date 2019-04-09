---
title: 'Como: Definir o renderizador ToolStrip para um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 857d5ea3771b098d4edcbd7b24f1e6feaf3ec2cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083070"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="1c3a1-102">Como: Definir o renderizador ToolStrip para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="1c3a1-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="1c3a1-103">Você pode personalizar a aparência de sua <xref:System.Windows.Forms.ToolStrip> controla individualmente ou para todos os <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c3a1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c3a1-104">Example</span></span>  
 <span data-ttu-id="1c3a1-105">O exemplo de código a seguir demonstra como aplicar seletivamente um renderizador personalizado para um <xref:System.Windows.Forms.ToolStrip> controle e um <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="1c3a1-106">Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, selecione o escopo de renderização personalizada do <xref:System.Windows.Forms.ComboBox> controle.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="1c3a1-107">Clique em **Aplicar** para definir o renderizador.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="1c3a1-108">Para ver a renderização do item de menu personalizado, selecione a <xref:System.Windows.Forms.MenuStrip> opção de <xref:System.Windows.Forms.ComboBox> de controle, clique em **aplicar**e, em seguida, abra o **arquivo** item de menu.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="1c3a1-109">Defina o <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para aplicar um renderizador personalizado a todos os <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="1c3a1-110">Defina as <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriedade para aplicar um renderizador personalizado a um indivíduo <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c3a1-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1c3a1-111">Compiling the Code</span></span>  
 <span data-ttu-id="1c3a1-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1c3a1-112">This example requires:</span></span>  
  
-   <span data-ttu-id="1c3a1-113">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1c3a1-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1c3a1-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1c3a1-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1c3a1-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3a1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c3a1-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="1c3a1-117">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1c3a1-117">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
