---
title: Controles constituintes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918423"
---
# <a name="constituent-controls"></a>Controles constituintes
Os controles que compõem um controle de usuário ou *controles membros* como são denominados, são relativamente inflexíveis quando se trata de renderização de elementos gráficos personalizados. Todos os controles de Windows Forms manipulam sua própria renderização <xref:System.Windows.Forms.Control.OnPaint%2A> por meio de seu próprio método. Como esse método é protegido, ele não está acessível para o desenvolvedor e, portanto, não pode ser impedido de ser executado quando o controle é pintado. Isso não significa, no entanto, que não é possível adicionar código para afetar a aparência dos controles membros. A renderização adicional pode ser realizada adicionando um manipulador de eventos. Por exemplo, suponha que você estivesse criando um <xref:System.Windows.Forms.UserControl> com um botão chamado `MyButton`. Se desejar ter renderização adicional além do que foi fornecido pelo <xref:System.Web.UI.WebControls.Button>, você adicionaria código ao seu controle de usuário semelhante ao seguinte:  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> Alguns controles de Windows Forms, <xref:System.Windows.Forms.TextBox>como, são pintados diretamente pelo Windows. Nesses casos, o <xref:System.Windows.Forms.Control.OnPaint%2A> método nunca é chamado e, portanto, o exemplo acima nunca será chamado.  
  
 Isso cria um método que é executado sempre que o evento `MyButton.Paint` é executado, conferindo, assim, uma representação gráfica adicional ao controle. Observe que isso não impede a execução de `MyButton.OnPaint` e, portanto, toda pintura normalmente executada por um botão será realizada além da sua pintura personalizada. Para obter detalhes sobre a tecnologia GDI+ e a renderização personalizada, consulte [Criando imagens gráficas com GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Se desejar ter uma representação exclusiva do seu controle, a melhor opção será criar um controle herdado e escrever código de renderização personalizada para ele. Para ver mais detalhes, consulte [Controles desenhados pelo usuário](user-drawn-controls.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Controles desenhados pelo usuário](user-drawn-controls.md)
- [Como: Criar objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
