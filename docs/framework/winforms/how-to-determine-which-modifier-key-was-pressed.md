---
title: 'Como: determinar qual tecla modificadora foi pressionada'
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
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964319"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Como: determinar qual tecla modificadora foi pressionada
Quando você cria um aplicativo que aceita a digitação do usuário, também é recomendável monitorar as teclas modificadoras como SHIFT, ALT e CTRL. Quando uma tecla modificadora for pressionada junto com outras teclas, ou com cliques do mouse, seu aplicativo pode responder adequadamente. Por exemplo, se a letra S for pressionada, isso poderá simplesmente fazer um “s” aparecer na tela, mas se as teclas CTRL + S forem pressionadas, o documento atual poderá ser salvo. Se você manipular o <xref:System.Windows.Forms.Control.KeyDown> evento, a <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriedade de <xref:System.Windows.Forms.KeyEventArgs> recebido pelo manipulador de eventos especifica quais teclas modificadoras são pressionadas. Como alternativa, a <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriedade de <xref:System.Windows.Forms.KeyEventArgs> especifica o caractere que foi pressionado, bem como quaisquer chaves de modificador combinadas com um OR-bit. No entanto, se você estiver <xref:System.Windows.Forms.Control.KeyPress> manipulando o evento ou um evento do mouse, o manipulador de eventos não receberá essas informações. Nesse caso, você deve usar a <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriedade <xref:System.Windows.Forms.Control> da classe. Em ambos os casos, você deve executar uma e/ou um <xref:System.Windows.Forms.Keys> valor apropriado e o valor que você está testando. A <xref:System.Windows.Forms.Keys> Enumeração oferece variações de cada chave de modificador, portanto, é importante que você execute o bit e o com o valor correto. Por exemplo, a tecla Shift é representada por <xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>e <xref:System.Windows.Forms.Keys.LShiftKey> o valor correto para testar o deslocamento como uma chave de modificador é <xref:System.Windows.Forms.Keys.Shift>. Da mesma forma, para testar CTRL e Alt como modificadores, você deve <xref:System.Windows.Forms.Keys.Control> usar <xref:System.Windows.Forms.Keys.Alt> os valores e, respectivamente.  
  
> [!NOTE]
> Visual Basic programadores também podem acessar informações de chave por <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> meio da propriedade  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Determinar qual tecla modificadora foi pressionada  
  
- Use o operador `AND` nonbit com <xref:System.Windows.Forms.Control.ModifierKeys%2A> a propriedade <xref:System.Windows.Forms.Keys> e um valor da enumeração para determinar se uma tecla modificadora específica é pressionada. O exemplo de código a seguir mostra como determinar se a tecla Shift é pressionada <xref:System.Windows.Forms.Control.KeyPress> dentro de um manipulador de eventos.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Entrada do teclado em um aplicativo dos Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Como: Determinar se CapsLock está no Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
