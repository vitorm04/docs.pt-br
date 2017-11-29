---
title: Como implementar um ToolStripRenderer personalizado
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
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd8953d6fe2e4a22e6c3b5fcc294855ef3a1c8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="d465d-102">Como implementar um ToolStripRenderer personalizado</span><span class="sxs-lookup"><span data-stu-id="d465d-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="d465d-103">Você pode personalizar a aparência de um <xref:System.Windows.Forms.ToolStrip> controle implementando uma classe que deriva de <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="d465d-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="d465d-104">Isso oferece a flexibilidade para criar uma aparência diferente da aparência fornecida a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> e <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span><span class="sxs-lookup"><span data-stu-id="d465d-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d465d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d465d-105">Example</span></span>  
 <span data-ttu-id="d465d-106">O exemplo de código a seguir demonstra como implementar um personalizado <xref:System.Windows.Forms.ToolStripRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="d465d-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="d465d-107">Neste exemplo, o controle `GridStrip` implementa um quebra-cabeça de bloco deslizante, que permite que o usuário mova os blocos em um layout de tabela para formar uma imagem.</span><span class="sxs-lookup"><span data-stu-id="d465d-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="d465d-108">Um personalizado <xref:System.Windows.Forms.ToolStrip> controle organiza seus <xref:System.Windows.Forms.ToolStripButton> controles em um layout de grade.</span><span class="sxs-lookup"><span data-stu-id="d465d-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="d465d-109">O layout contém uma célula vazia, na qual o usuário pode deslizar um bloco adjacente usando uma operação do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="d465d-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="d465d-110">Blocos que o usuário pode mover são realçados.</span><span class="sxs-lookup"><span data-stu-id="d465d-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="d465d-111">A classe `GridStripRenderer` personaliza três aspectos da aparência do controle `GridStrip`:</span><span class="sxs-lookup"><span data-stu-id="d465d-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="d465d-112">Borda `GridStrip`</span><span class="sxs-lookup"><span data-stu-id="d465d-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="d465d-113">Borda <xref:System.Windows.Forms.ToolStripButton></span><span class="sxs-lookup"><span data-stu-id="d465d-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="d465d-114"><xref:System.Windows.Forms.ToolStripButton>imagem</span><span class="sxs-lookup"><span data-stu-id="d465d-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d465d-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d465d-115">Compiling the Code</span></span>  
 <span data-ttu-id="d465d-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d465d-116">This example requires:</span></span>  
  
-   <span data-ttu-id="d465d-117">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d465d-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d465d-118">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="d465d-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d465d-119">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="d465d-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="d465d-120">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="d465d-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d465d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d465d-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="d465d-122">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d465d-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
