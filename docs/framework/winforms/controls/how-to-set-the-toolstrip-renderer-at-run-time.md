---
title: 'Como: Definir o renderizador ToolStrip em tempo de execução'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
ms.openlocfilehash: ddedae5bd7a58b7d8babca7f92bb261a10d2ddee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511989"
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="28c50-102">Como: Definir o renderizador ToolStrip em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="28c50-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="28c50-103">Você pode personalizar a aparência de sua <xref:System.Windows.Forms.ToolStrip> controle criando um personalizado `ProfessionalColorTable` classe.</span><span class="sxs-lookup"><span data-stu-id="28c50-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28c50-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28c50-104">Example</span></span>  
 <span data-ttu-id="28c50-105">O exemplo de código a seguir demonstra como criar um personalizado `ProfessionalColorTable` classe.</span><span class="sxs-lookup"><span data-stu-id="28c50-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="28c50-106">Essa classe define os gradientes para um <xref:System.Windows.Forms.MenuStrip> e um <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="28c50-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="28c50-107">Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, clique em **alterar cores** para aplicar os gradientes definidos no personalizado `ProfessionalColorTable` classe.</span><span class="sxs-lookup"><span data-stu-id="28c50-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="28c50-108">Definindo uma classe personalizada ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="28c50-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="28c50-109">Os gradientes personalizados são definidos no `CustomProfessionalColors` classe.</span><span class="sxs-lookup"><span data-stu-id="28c50-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="28c50-110">Atribuir um renderizador personalizado</span><span class="sxs-lookup"><span data-stu-id="28c50-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="28c50-111">Criar um novo `ToolStripProfessionalRenderer` com um `CustomProfessionalColors` classe e o atribui a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="28c50-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28c50-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="28c50-112">Compiling the Code</span></span>  
 <span data-ttu-id="28c50-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="28c50-113">This example requires:</span></span>  
  
-   <span data-ttu-id="28c50-114">Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="28c50-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="28c50-115">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="28c50-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="28c50-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="28c50-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="28c50-117">Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="28c50-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c50-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28c50-118">See also</span></span>
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="28c50-119">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="28c50-119">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
