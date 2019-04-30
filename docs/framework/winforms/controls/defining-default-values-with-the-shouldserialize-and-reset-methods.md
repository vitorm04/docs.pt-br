---
title: Definindo valores padrão com o ShouldSerialize e os métodos de redefinição
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: f1f5a668c5d4f52ef7dd9f60a31c04f2173165f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972361"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definindo valores padrão com o ShouldSerialize e os métodos de redefinição
`ShouldSerialize` e `Reset` são métodos opcionais que você pode fornecer para uma propriedade, caso ela não tenha um valor padrão simples. Se a propriedade tem um valor padrão simples, você deve aplicar o <xref:System.ComponentModel.DefaultValueAttribute> e forneça o valor padrão para o construtor de classe de atributo em vez disso. Qualquer um desses mecanismos habilita os recursos a seguir no designer:  
  
- A propriedade fornecerá uma indicação visual no navegador de propriedades se tiver sido modificado de seu valor padrão.  
  
- O usuário pode clicar com o botão direito do mouse na propriedade e escolher **Redefinir** para restaurar a propriedade para o valor padrão.  
  
- O designer gera um código mais eficiente.  
  
    > [!NOTE]
    >  Alguma se aplicar a <xref:System.ComponentModel.DefaultValueAttribute> ou forneça `Reset` *PropertyName* e `ShouldSerialize` *PropertyName* métodos. Não use os dois.  
  
 O método `Reset`*PropertyName* define uma propriedade para o valor padrão, conforme mostrado no seguinte fragmento de código.  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  Se uma propriedade não tem um `Reset` método, não é marcado com um <xref:System.ComponentModel.DefaultValueAttribute>e não tem um valor padrão fornecido na sua declaração, o `Reset` opção para essa propriedade está desabilitada no menu de atalho do **propriedades** janela do Designer de formulários do Windows no Visual Studio.  
  
 Designers como o Visual Studio usam o `ShouldSerialize` *PropertyName* método para verificar se uma propriedade foi alterada do seu valor padrão e escrever código no formulário apenas se uma propriedade for alterado, permitindo, portanto, um código mais eficiente geração. Por exemplo:  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 Segue um exemplo de código completo.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 Nesse caso, mesmo quando o valor da variável particular acessada pela `MyFont` é de propriedade `null`, o navegador de propriedade não exibe `null`; em vez disso, ele exibe o <xref:System.Windows.Forms.Control.Font%2A> propriedade do pai, se não for `null`, ou o padrão <xref:System.Windows.Forms.Control.Font%2A> valor definido na <xref:System.Windows.Forms.Control>. Assim, o valor padrão para `MyFont` não pode ser simplesmente definido e um <xref:System.ComponentModel.DefaultValueAttribute> não pode ser aplicado a essa propriedade. Em vez disso, os métodos `ShouldSerialize` e `Reset` devem ser implementados para a propriedade `MyFont`.  
  
## <a name="see-also"></a>Consulte também

- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
- [Definindo uma propriedade](defining-a-property-in-windows-forms-controls.md)
- [Eventos alterados por propriedade](property-changed-events.md)
