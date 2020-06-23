---
title: 'Como: manipular a entrada do teclado no nível do formulário'
description: Saiba como lidar com a entrada de teclado para sua Windows Forms no nível de formulário, antes que as mensagens cheguem a um controle.
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
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904150"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="6e31f-103">Como: manipular a entrada do teclado no nível do formulário</span><span class="sxs-lookup"><span data-stu-id="6e31f-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="6e31f-104">Os Windows Forms proporcionam a capacidade de manipular mensagens de teclado no nível do formulário, antes que as mensagens cheguem a um controle.</span><span class="sxs-lookup"><span data-stu-id="6e31f-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="6e31f-105">Este tópico mostra como realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="6e31f-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="6e31f-106">Como manipular uma mensagem do teclado no nível do formulário</span><span class="sxs-lookup"><span data-stu-id="6e31f-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="6e31f-107">Manipule o <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> evento ou do formulário de inicialização e defina a <xref:System.Windows.Forms.Form.KeyPreview%2A> Propriedade do formulário como para `true` que as mensagens do teclado sejam recebidas pelo formulário antes de alcançarem controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="6e31f-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="6e31f-108">O exemplo de código a seguir trata o <xref:System.Windows.Forms.Control.KeyPress> evento detectando todas as chaves de número e consumindo ' 1 ', ' 4 ' e ' 7 '.</span><span class="sxs-lookup"><span data-stu-id="6e31f-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="6e31f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e31f-109">Example</span></span>  
 <span data-ttu-id="6e31f-110">O exemplo de código a seguir é o aplicativo completo para o exemplo acima.</span><span class="sxs-lookup"><span data-stu-id="6e31f-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="6e31f-111">O aplicativo inclui um <xref:System.Windows.Forms.TextBox> juntamente com vários outros controles que permitem que você mova o foco do <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="6e31f-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6e31f-112">O <xref:System.Windows.Forms.Control.KeyPress> evento da principal <xref:System.Windows.Forms.Form> consome ' 1 ', ' 4 ' e ' 7 ', e o <xref:System.Windows.Forms.Control.KeyPress> evento de <xref:System.Windows.Forms.TextBox> consome ' 2 ', ' 5 ' e ' 8 ' ao exibir as chaves restantes.</span><span class="sxs-lookup"><span data-stu-id="6e31f-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="6e31f-113">Compare a <xref:System.Windows.Forms.MessageBox> saída quando você pressiona uma tecla numérica enquanto o <xref:System.Windows.Forms.TextBox> foco <xref:System.Windows.Forms.MessageBox> está na saída quando você pressiona uma tecla numérica enquanto o foco está em um dos outros controles.</span><span class="sxs-lookup"><span data-stu-id="6e31f-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e31f-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6e31f-114">Compiling the Code</span></span>  
 <span data-ttu-id="6e31f-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6e31f-115">This example requires:</span></span>  
  
- <span data-ttu-id="6e31f-116">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6e31f-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e31f-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="6e31f-117">See also</span></span>

- [<span data-ttu-id="6e31f-118">Entrada do teclado em um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e31f-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
