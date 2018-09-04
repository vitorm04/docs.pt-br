---
title: Como fornecer itens de menu padrão para um formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: bf43d27ed728d11b5cde5b9250cfc4614077ed94
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512984"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="cfb20-102">Como fornecer itens de menu padrão para um formulário</span><span class="sxs-lookup"><span data-stu-id="cfb20-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="cfb20-103">Você pode fornecer um menu padrão para os formulários com o <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="cfb20-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="cfb20-104">Há suporte abrangente para este recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfb20-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="cfb20-105">Consulte também [instruções passo a passo: fornecendo itens de Menu padrão para um formulário](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="cfb20-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfb20-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfb20-106">Example</span></span>  
 <span data-ttu-id="cfb20-107">O exemplo de código a seguir demonstra como usar um <xref:System.Windows.Forms.MenuStrip> controle para criar um formulário com um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="cfb20-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="cfb20-108">Seleções de item de menu são exibidas em um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="cfb20-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cfb20-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="cfb20-109">Compiling the Code</span></span>  
 <span data-ttu-id="cfb20-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="cfb20-110">This example requires:</span></span>  
  
-   <span data-ttu-id="cfb20-111">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cfb20-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cfb20-112">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cfb20-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cfb20-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="cfb20-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="cfb20-114">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cfb20-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb20-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfb20-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="cfb20-116">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="cfb20-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
