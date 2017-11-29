---
title: Como determinar qual tecla modificadora foi pressionada
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fdc93063bbc8c9428f2f01c6cd5c0578e77ab01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Como determinar qual tecla modificadora foi pressionada
Quando você cria um aplicativo que aceita a digitação do usuário, também é recomendável monitorar as teclas modificadoras como SHIFT, ALT e CTRL. Quando uma tecla modificadora for pressionada junto com outras teclas, ou com cliques do mouse, seu aplicativo pode responder adequadamente. Por exemplo, se a letra S for pressionada, isso poderá simplesmente fazer um “s” aparecer na tela, mas se as teclas CTRL + S forem pressionadas, o documento atual poderá ser salvo. Se você tratar o <xref:System.Windows.Forms.Control.KeyDown> evento, o <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriedade do <xref:System.Windows.Forms.KeyEventArgs> recebida pelo evento manipulador Especifica quais teclas modificadoras são pressionadas. Como alternativa, o <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriedade <xref:System.Windows.Forms.KeyEventArgs> Especifica o caractere que foi pressionado, bem como qualquer tecla modificadora combinada com um OR bit a bit. No entanto, se você estiver tratando o <xref:System.Windows.Forms.Control.KeyPress> evento ou um evento do mouse, o manipulador de eventos não recebe essas informações. Nesse caso, você deve usar o <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriedade o <xref:System.Windows.Forms.Control> classe. Em ambos os casos, você deve executar um AND bit a bit dos <xref:System.Windows.Forms.Keys> valor e o valor que você está testando. O <xref:System.Windows.Forms.Keys> enumeração oferece variações de cada tecla modificadora, portanto, é importante que você execute o bit a bit e com o valor correto. Por exemplo, a tecla SHIFT é representada por <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> e <xref:System.Windows.Forms.Keys.LShiftKey> o valor correto para testar SHIFT como uma tecla modificadora <xref:System.Windows.Forms.Keys.Shift>. Da mesma forma testar CTLR e ALT como modificadoras você deve usar o <xref:System.Windows.Forms.Keys.Control> e <xref:System.Windows.Forms.Keys.Alt> valores, respectivamente.  
  
> [!NOTE]
>  Programadores de Visual Basic também podem acessar informações de chave por meio de <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> propriedade  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Determinar qual tecla modificadora foi pressionada  
  
-   Use o bit a bit `AND` operador com o <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriedade e um valor da <xref:System.Windows.Forms.Keys> enumeração para determinar se uma tecla modificadora em particular é pressionada. O exemplo de código a seguir mostra como determinar se a tecla SHIFT é pressionado dentro de um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Entrada do teclado em um aplicativo dos Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Como determinar se CapsLock está ativado no Visual Basic](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)
