---
title: Como manipular a entrada do teclado no nível do formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: a75c4f116b32499f9ba33dd863f2a5b6952a3e24
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492951"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="64193-102">Como manipular a entrada do teclado no nível do formulário</span><span class="sxs-lookup"><span data-stu-id="64193-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="64193-103">Os Windows Forms proporcionam a capacidade de manipular mensagens de teclado no nível do formulário, antes que as mensagens cheguem a um controle.</span><span class="sxs-lookup"><span data-stu-id="64193-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="64193-104">Este tópico mostra como realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="64193-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="64193-105">Como manipular uma mensagem do teclado no nível do formulário</span><span class="sxs-lookup"><span data-stu-id="64193-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="64193-106">Lidar com o <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> evento do formulário de inicialização e defina as <xref:System.Windows.Forms.Form.KeyPreview%2A> propriedade do formulário para `true` para que as mensagens do teclado são recebidas pelo formulário antes que elas atinjam os controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="64193-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="64193-107">O seguinte código de exemplo manipula o <xref:System.Windows.Forms.Control.KeyPress> eventos, detectando todas as teclas numéricas e consumindo '1', '4' e '7'.</span><span class="sxs-lookup"><span data-stu-id="64193-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="64193-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64193-108">Example</span></span>  
 <span data-ttu-id="64193-109">O exemplo de código a seguir é o aplicativo completo para o exemplo acima.</span><span class="sxs-lookup"><span data-stu-id="64193-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="64193-110">O aplicativo inclui um <xref:System.Windows.Forms.TextBox> juntamente com vários outros controles que permitem que você mova o foco do <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="64193-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="64193-111">O <xref:System.Windows.Forms.Control.KeyPress> eventos da janela principal <xref:System.Windows.Forms.Form> consome '1', '4' e '7' e o <xref:System.Windows.Forms.Control.KeyPress> evento do <xref:System.Windows.Forms.TextBox> consome '2', '5' e '8' e exibe as teclas restantes.</span><span class="sxs-lookup"><span data-stu-id="64193-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="64193-112">Comparar as <xref:System.Windows.Forms.MessageBox> de saída quando você pressiona uma tecla numérica enquanto o <xref:System.Windows.Forms.TextBox> tem o foco com o <xref:System.Windows.Forms.MessageBox> quando você pressiona uma tecla numérica enquanto o foco está em um dos outros controles de saída.</span><span class="sxs-lookup"><span data-stu-id="64193-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64193-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="64193-113">Compiling the Code</span></span>  
 <span data-ttu-id="64193-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="64193-114">This example requires:</span></span>  
  
-   <span data-ttu-id="64193-115">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="64193-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="64193-116">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="64193-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="64193-117">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="64193-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="64193-118">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="64193-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64193-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64193-119">See Also</span></span>  
 [<span data-ttu-id="64193-120">Entrada do teclado em um aplicativo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64193-120">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
