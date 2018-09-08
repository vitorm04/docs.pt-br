---
title: Como determinar qual tecla modificadora foi pressionada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: f73dea640bc2059353b2a250188b901f360ea750
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202031"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="2ab89-102">Como determinar qual tecla modificadora foi pressionada</span><span class="sxs-lookup"><span data-stu-id="2ab89-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="2ab89-103">Quando você cria um aplicativo que aceita a digitação do usuário, também é recomendável monitorar as teclas modificadoras como SHIFT, ALT e CTRL.</span><span class="sxs-lookup"><span data-stu-id="2ab89-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="2ab89-104">Quando uma tecla modificadora for pressionada junto com outras teclas, ou com cliques do mouse, seu aplicativo pode responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="2ab89-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="2ab89-105">Por exemplo, se a letra S for pressionada, isso poderá simplesmente fazer um “s” aparecer na tela, mas se as teclas CTRL + S forem pressionadas, o documento atual poderá ser salvo.</span><span class="sxs-lookup"><span data-stu-id="2ab89-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="2ab89-106">Se você tratar a <xref:System.Windows.Forms.Control.KeyDown> evento, o <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriedade do <xref:System.Windows.Forms.KeyEventArgs> recebida pelo evento manipulador Especifica quais teclas modificadoras são pressionadas.</span><span class="sxs-lookup"><span data-stu-id="2ab89-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="2ab89-107">Como alternativa, o <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriedade de <xref:System.Windows.Forms.KeyEventArgs> Especifica o caractere que foi pressionado, bem como quaisquer teclas modificadoras combinadas com um OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="2ab89-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="2ab89-108">No entanto, se você estiver tratando o <xref:System.Windows.Forms.Control.KeyPress> evento ou um evento de mouse, o manipulador de eventos não recebe essas informações.</span><span class="sxs-lookup"><span data-stu-id="2ab89-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="2ab89-109">Nesse caso, você deve usar o <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriedade do <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="2ab89-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="2ab89-110">Em ambos os casos, você deve executar um AND bit a bit de apropriado <xref:System.Windows.Forms.Keys> valor e o valor que você está testando.</span><span class="sxs-lookup"><span data-stu-id="2ab89-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="2ab89-111">O <xref:System.Windows.Forms.Keys> enumeração oferece variações de cada tecla modificadora, portanto, é importante que você execute uma operação bit a bit e com o valor correto.</span><span class="sxs-lookup"><span data-stu-id="2ab89-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="2ab89-112">Por exemplo, a tecla SHIFT é representada por <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> e <xref:System.Windows.Forms.Keys.LShiftKey> o valor correto para testar SHIFT como uma tecla modificadora <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="2ab89-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="2ab89-113">Da mesma forma testar CTLR e ALT como modificadoras você deve usar o <xref:System.Windows.Forms.Keys.Control> e <xref:System.Windows.Forms.Keys.Alt> valores, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2ab89-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ab89-114">Os programadores de Visual Basic também podem acessar informações de chave por meio de <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="2ab89-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="2ab89-115">Determinar qual tecla modificadora foi pressionada</span><span class="sxs-lookup"><span data-stu-id="2ab89-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="2ab89-116">Use o bit a bit `AND` operador com o <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriedade e um valor da <xref:System.Windows.Forms.Keys> enumeração para determinar se uma tecla modificadora específica é pressionada.</span><span class="sxs-lookup"><span data-stu-id="2ab89-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="2ab89-117">O exemplo de código a seguir mostra como determinar se a tecla SHIFT está pressionada em um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab89-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2ab89-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ab89-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="2ab89-119">Entrada do teclado em um aplicativo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ab89-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="2ab89-120">Como determinar se CapsLock está ativado no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ab89-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](https://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
