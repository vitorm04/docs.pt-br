---
title: Como definir o renderizador ToolStrip para um aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8185adbf7d8979f03b3d0428fcc2ec0941c7999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="571d5-102">Como definir o renderizador ToolStrip para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="571d5-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="571d5-103">Você pode personalizar a aparência de seu <xref:System.Windows.Forms.ToolStrip> controla individualmente ou todos os <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="571d5-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="571d5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="571d5-104">Example</span></span>  
 <span data-ttu-id="571d5-105">O exemplo de código a seguir demonstra como aplicar seletivamente um renderizador personalizado para um <xref:System.Windows.Forms.ToolStrip> controle e um <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="571d5-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="571d5-106">Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, selecione o escopo de rending personalizado do <xref:System.Windows.Forms.ComboBox> controle.</span><span class="sxs-lookup"><span data-stu-id="571d5-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="571d5-107">Clique em **Aplicar** para definir o renderizador.</span><span class="sxs-lookup"><span data-stu-id="571d5-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="571d5-108">Para ver o processamento do item de menu personalizados, selecione o <xref:System.Windows.Forms.MenuStrip> opção o <xref:System.Windows.Forms.ComboBox> de controle, clique em **aplicar**e, em seguida, abra o **arquivo** item de menu.</span><span class="sxs-lookup"><span data-stu-id="571d5-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="571d5-109">Definir o <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> aplicar um renderizador personalizado para todos o <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="571d5-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="571d5-110">Definir o <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> aplicar um renderizador personalizado a um indivíduo <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="571d5-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="571d5-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="571d5-111">Compiling the Code</span></span>  
 <span data-ttu-id="571d5-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="571d5-112">This example requires:</span></span>  
  
-   <span data-ttu-id="571d5-113">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="571d5-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="571d5-114">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="571d5-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="571d5-115">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="571d5-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="571d5-116">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="571d5-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571d5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="571d5-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="571d5-118">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="571d5-118">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
