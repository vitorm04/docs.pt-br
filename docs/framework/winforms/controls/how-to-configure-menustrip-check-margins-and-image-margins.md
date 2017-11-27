---
title: "Como configurar margens de imagem e margens de verificação MenuStrip"
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
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6fc37658606d5617334e02fd838a9c9fc679a1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="12822-102">Como configurar margens de imagem e margens de verificação MenuStrip</span><span class="sxs-lookup"><span data-stu-id="12822-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="12822-103">Você pode personalizar um <xref:System.Windows.Forms.MenuStrip> definindo o <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> e <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> propriedades em várias combinações.</span><span class="sxs-lookup"><span data-stu-id="12822-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12822-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12822-104">Example</span></span>  
 <span data-ttu-id="12822-105">O exemplo de código a seguir demonstra como definir e personalizar o <xref:System.Windows.Forms.ContextMenuStrip> verificar margens de imagem e margens.</span><span class="sxs-lookup"><span data-stu-id="12822-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="12822-106">O procedimento é o mesmo para um <xref:System.Windows.Forms.ContextMenuStrip> ou <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="12822-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12822-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="12822-107">Compiling the Code</span></span>  
 <span data-ttu-id="12822-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="12822-108">This example requires:</span></span>  
  
-   <span data-ttu-id="12822-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="12822-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="12822-110">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="12822-110">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="12822-111">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="12822-111">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="12822-112">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="12822-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12822-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12822-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="12822-114">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="12822-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="12822-115">Como habilitar margens de verificação e de imagem em controles ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="12822-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
