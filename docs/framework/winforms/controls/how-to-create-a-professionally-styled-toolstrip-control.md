---
title: 'Como: Criar um controle ToolStrip com estilo profissional'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6da6e113867efed79dfcd02f3b89ee1f9ae13c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746649"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="aeb33-102">Como: Criar um controle ToolStrip com estilo profissional</span><span class="sxs-lookup"><span data-stu-id="aeb33-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="aeb33-103">Você pode dar a seu aplicativo <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional e o comportamento (aparência) ao escrever sua própria classe que deriva de <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tipo.</span><span class="sxs-lookup"><span data-stu-id="aeb33-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="aeb33-104">Há suporte abrangente para este recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aeb33-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="aeb33-105">Confira [Passo a passo: Criando um controle ToolStrip com estilo profissional](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="aeb33-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb33-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aeb33-106">Example</span></span>  
 <span data-ttu-id="aeb33-107">O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.ToolStrip> controles para criar um controle composto que imita a **painel de navegação** fornecidas pelo Microsoft® Outlook®.</span><span class="sxs-lookup"><span data-stu-id="aeb33-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aeb33-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aeb33-108">Compiling the Code</span></span>  
 <span data-ttu-id="aeb33-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="aeb33-109">This example requires:</span></span>  
  
- <span data-ttu-id="aeb33-110">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="aeb33-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="aeb33-111">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aeb33-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="aeb33-112">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="aeb33-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="aeb33-113">Consulte também [passo a passo: Criando um controle ToolStrip com estilo profissional](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="aeb33-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb33-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aeb33-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="aeb33-115">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="aeb33-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="aeb33-116">Como: Fornecer itens de Menu padrão para um formulário</span><span class="sxs-lookup"><span data-stu-id="aeb33-116">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
