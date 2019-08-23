---
title: 'Como: modificar a entrada do teclado para um controle padrão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964285"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="136ef-102">Como: modificar a entrada do teclado para um controle padrão</span><span class="sxs-lookup"><span data-stu-id="136ef-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="136ef-103">O Windows Forms fornece a capacidade de consumir e modificar as entradas do teclado.</span><span class="sxs-lookup"><span data-stu-id="136ef-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="136ef-104">Consumir uma tecla significa tratá-la dentro de um método ou manipulador de eventos para que outros métodos e eventos mais adiante na fila de mensagens não recebam o valor da tecla.</span><span class="sxs-lookup"><span data-stu-id="136ef-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="136ef-105">Modificar uma tecla significa modificar o valor de uma tecla para que os métodos e manipuladores de eventos mais adiante na fila de mensagens recebam um valor de tecla diferente.</span><span class="sxs-lookup"><span data-stu-id="136ef-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="136ef-106">Este tópico mostra como realizar essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="136ef-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="136ef-107">Consumir uma tecla</span><span class="sxs-lookup"><span data-stu-id="136ef-107">To consume a key</span></span>  
  
- <span data-ttu-id="136ef-108">Em um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos, defina <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> a propriedade da <xref:System.Windows.Forms.KeyPressEventArgs> classe como `true`.</span><span class="sxs-lookup"><span data-stu-id="136ef-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="136ef-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="136ef-109">-or-</span></span>  
  
     <span data-ttu-id="136ef-110">Em um <xref:System.Windows.Forms.Control.KeyDown> manipulador de eventos, defina <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> a propriedade da <xref:System.Windows.Forms.KeyEventArgs> classe como `true`.</span><span class="sxs-lookup"><span data-stu-id="136ef-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="136ef-111">Definir a <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.Control.KeyDown> Propriedade no manipulador de eventos não impede que os <xref:System.Windows.Forms.Control.KeyPress> eventos <xref:System.Windows.Forms.Control.KeyUp> e sejam gerados para o pressionamento de teclas atual.</span><span class="sxs-lookup"><span data-stu-id="136ef-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="136ef-112">Use a <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> propriedade para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="136ef-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="136ef-113">O exemplo a seguir é um trecho de `switch` uma instrução que examina a <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> Propriedade do <xref:System.Windows.Forms.KeyPressEventArgs> recebido por um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="136ef-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="136ef-114">Esse código consome as teclas dos caracteres “A” e “a”.</span><span class="sxs-lookup"><span data-stu-id="136ef-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="136ef-115">Modificar uma tecla de caractere padrão</span><span class="sxs-lookup"><span data-stu-id="136ef-115">To modify a standard character key</span></span>  
  
- <span data-ttu-id="136ef-116">Em um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos, defina <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> a propriedade da <xref:System.Windows.Forms.KeyPressEventArgs> classe como o valor da nova chave de caractere.</span><span class="sxs-lookup"><span data-stu-id="136ef-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="136ef-117">O exemplo a seguir é um trecho de uma instrução `switch` que modifica “B” para “A” e “b” para “a”.</span><span class="sxs-lookup"><span data-stu-id="136ef-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="136ef-118">Observe que a <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> propriedade <xref:System.Windows.Forms.KeyPressEventArgs> do parâmetro é definida como `false`, de forma que o novo valor de chave seja propagado para outros métodos e eventos na fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="136ef-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="136ef-119">Modificar uma tecla não caractere</span><span class="sxs-lookup"><span data-stu-id="136ef-119">To modify a noncharacter key</span></span>  
  
- <span data-ttu-id="136ef-120">Substitua um <xref:System.Windows.Forms.Control> método que processa mensagens do Windows, detecte a mensagem WM_KEYDOWN ou WM_SYSKEYDOWN e <xref:System.Windows.Forms.Message.WParam%2A> defina a propriedade <xref:System.Windows.Forms.Message> do parâmetro para <xref:System.Windows.Forms.Keys> o valor que representa a nova chave não caractere.</span><span class="sxs-lookup"><span data-stu-id="136ef-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="136ef-121">O exemplo de código a seguir demonstra como substituir <xref:System.Windows.Forms.Control.PreProcessMessage%2A> o método de um controle para detectar as teclas F1 por F9 e modificar qualquer pressionamento de tecla F3 para F1.</span><span class="sxs-lookup"><span data-stu-id="136ef-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="136ef-122">Para obter mais informações <xref:System.Windows.Forms.Control> sobre os métodos que você pode substituir para interceptar mensagens do teclado, consulte [entrada do usuário em um aplicativo Windows Forms](user-input-in-a-windows-forms-application.md) e [como funciona a entrada do teclado](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="136ef-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="136ef-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="136ef-123">Example</span></span>  
 <span data-ttu-id="136ef-124">O exemplo de código a seguir é o aplicativo completo para os exemplos de código nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="136ef-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="136ef-125">O aplicativo usa um controle personalizado derivado da <xref:System.Windows.Forms.TextBox> classe para consumir e modificar a entrada do teclado.</span><span class="sxs-lookup"><span data-stu-id="136ef-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="136ef-126">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="136ef-126">Compiling the Code</span></span>  
 <span data-ttu-id="136ef-127">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="136ef-127">This example requires:</span></span>  
  
- <span data-ttu-id="136ef-128">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="136ef-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136ef-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="136ef-129">See also</span></span>

- [<span data-ttu-id="136ef-130">Entrada do teclado em um aplicativo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136ef-130">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="136ef-131">Entrada do usuário em um aplicativo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="136ef-131">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="136ef-132">Como a entrada do teclado funciona</span><span class="sxs-lookup"><span data-stu-id="136ef-132">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
