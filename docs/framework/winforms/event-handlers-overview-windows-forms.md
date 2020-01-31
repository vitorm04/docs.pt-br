---
title: Visão geral de manipuladores de eventos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743465"
---
# <a name="event-handlers-overview-windows-forms"></a>Visão geral de manipuladores de eventos (Windows Forms)
Um manipulador de eventos é um método que está associado a um evento. Quando o evento é gerado, o código no manipulador de eventos é executado. Cada manipulador de eventos fornece dois parâmetros que permitem manipular o evento corretamente. O exemplo a seguir mostra um manipulador de eventos para um evento de <xref:System.Windows.Forms.Control.Click> do controle de <xref:System.Windows.Forms.Button>.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 No primeiro parâmetro, `sender`, fornece uma referência ao objeto que gerou o evento. No exemplo acima, o segundo parâmetro, `e`, passa um objeto específico para o evento que está sendo manipulado. Consultando as propriedades do objeto (e, às vezes, seus métodos), é possível obter informações como o local do mouse para eventos de mouse ou dados que estão sendo transferidos em eventos do tipo "arrastar e soltar".  
  
 Normalmente, cada evento produz um manipulador de eventos com um tipo de objeto de evento diferente para o segundo parâmetro. Alguns manipuladores de eventos, como aqueles para os eventos <xref:System.Windows.Forms.Control.MouseDown> e <xref:System.Windows.Forms.Control.MouseUp>, têm o mesmo tipo de objeto para o segundo parâmetro. Para esses tipos de eventos, você pode usar o mesmo manipulador de eventos para manipular ambos os eventos.  
  
 Você também pode usar o mesmo manipulador de eventos para manipular o mesmo evento em controles diferentes. Por exemplo, se você tiver um grupo de controles de <xref:System.Windows.Forms.RadioButton> em um formulário, poderá criar um único manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> e ter cada evento de <xref:System.Windows.Forms.Control.Click> de controle associado ao manipulador de eventos único. Para obter mais informações, consulte [Como conectar vários eventos a um único manipulador de eventos nos Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Veja também

- [Criando manipuladores de eventos no Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Visão geral de eventos](events-overview-windows-forms.md)
