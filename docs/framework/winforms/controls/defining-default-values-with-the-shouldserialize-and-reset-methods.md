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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969091"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definindo valores padrão com o ShouldSerialize e os métodos de redefinição
`ShouldSerialize` e `Reset` são métodos opcionais que você pode fornecer para uma propriedade, caso ela não tenha um valor padrão simples. Se a propriedade tiver um valor padrão simples, você deverá aplicar o <xref:System.ComponentModel.DefaultValueAttribute> e fornecer o valor padrão ao construtor de classe de atributo em vez disso. Qualquer um desses mecanismos habilita os recursos a seguir no designer:

- A propriedade fornecerá uma indicação visual no navegador de propriedades se tiver sido modificado de seu valor padrão.

- O usuário pode clicar com o botão direito do mouse na propriedade e escolher **Redefinir** para restaurar a propriedade para o valor padrão.

- O designer gera um código mais eficiente.

    > [!NOTE]
    > Aplique ou forneça <xref:System.ComponentModel.DefaultValueAttribute> `Reset`os métodos *PropertyName* e `ShouldSerialize` *PropertyName* . Não use os dois.

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
> Se uma propriedade não tiver `Reset` um método, não estiver marcada com um <xref:System.ComponentModel.DefaultValueAttribute>e não tiver um valor padrão fornecido em sua declaração, a `Reset` opção dessa propriedade será desabilitada no menu de atalho da janela **Propriedades** do o Designer de Formulários do Windows no Visual Studio.

 Designers como o Visual Studio usam o `ShouldSerialize`método *PropertyName* para verificar se uma propriedade foi alterada de seu valor padrão e gravar código no formulário somente se uma propriedade for alterada, permitindo assim uma geração de código mais eficiente. Por exemplo:

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

 Nesse caso, mesmo quando o valor da variável privada acessado `MyFont` pela propriedade é `null`, o navegador de propriedades não é exibido `null`; em vez disso, ele <xref:System.Windows.Forms.Control.Font%2A> exibe a propriedade do pai, se não `null`for, ou o valor <xref:System.Windows.Forms.Control.Font%2A> padrão definido em <xref:System.Windows.Forms.Control>. Portanto, o valor padrão `MyFont` para não pode ser simplesmente definido, <xref:System.ComponentModel.DefaultValueAttribute> e um não pode ser aplicado a essa propriedade. Em vez disso, os métodos `ShouldSerialize` e `Reset` devem ser implementados para a propriedade `MyFont`.

## <a name="see-also"></a>Consulte também

- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
- [Definindo uma propriedade](defining-a-property-in-windows-forms-controls.md)
- [Eventos alterados por propriedade](property-changed-events.md)
