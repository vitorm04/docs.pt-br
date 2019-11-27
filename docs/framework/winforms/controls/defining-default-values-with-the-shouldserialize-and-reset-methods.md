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
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336758"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="8d20a-102">Definindo valores padrão com o ShouldSerialize e os métodos de redefinição</span><span class="sxs-lookup"><span data-stu-id="8d20a-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="8d20a-103">`ShouldSerialize` e `Reset` são métodos opcionais que você pode fornecer para uma propriedade, caso ela não tenha um valor padrão simples.</span><span class="sxs-lookup"><span data-stu-id="8d20a-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="8d20a-104">Se a propriedade tiver um valor padrão simples, você deverá aplicar o <xref:System.ComponentModel.DefaultValueAttribute> e fornecer o valor padrão ao construtor de classe de atributo em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8d20a-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="8d20a-105">Qualquer um desses mecanismos habilita os recursos a seguir no designer:</span><span class="sxs-lookup"><span data-stu-id="8d20a-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="8d20a-106">A propriedade fornecerá uma indicação visual no navegador de propriedades se tiver sido modificado de seu valor padrão.</span><span class="sxs-lookup"><span data-stu-id="8d20a-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="8d20a-107">O usuário pode clicar com o botão direito do mouse na propriedade e escolher **Redefinir** para restaurar a propriedade para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="8d20a-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="8d20a-108">O designer gera um código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="8d20a-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d20a-109">Aplique os <xref:System.ComponentModel.DefaultValueAttribute> ou forneça `Reset`*PropertyName* e `ShouldSerialize`métodos *PropertyName* .</span><span class="sxs-lookup"><span data-stu-id="8d20a-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="8d20a-110">Não use os dois.</span><span class="sxs-lookup"><span data-stu-id="8d20a-110">Do not use both.</span></span>

 <span data-ttu-id="8d20a-111">O método `Reset`*PropertyName* define uma propriedade para o valor padrão, conforme mostrado no seguinte fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="8d20a-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="8d20a-112">Se uma propriedade não tiver um método `Reset`, não estiver marcada com uma <xref:System.ComponentModel.DefaultValueAttribute>e não tiver um valor padrão fornecido em sua declaração, a opção `Reset` para essa propriedade será desabilitada no menu de atalho da janela **Propriedades** do designer de formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d20a-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="8d20a-113">Designers como o Visual Studio usam o método `ShouldSerialize`*PropertyName* para verificar se uma propriedade foi alterada de seu valor padrão e gravar código no formulário somente se uma propriedade for alterada, permitindo assim uma geração de código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="8d20a-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="8d20a-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d20a-114">For example:</span></span>

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

 <span data-ttu-id="8d20a-115">Segue um exemplo de código completo.</span><span class="sxs-lookup"><span data-stu-id="8d20a-115">A complete code example follows.</span></span>

```vb
Option Explicit
Option Strict

Imports System.Drawing
Imports System.Windows.Forms

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
using System.Drawing;
using System.Windows.Forms;

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

 <span data-ttu-id="8d20a-116">Nesse caso, mesmo quando o valor da variável privada acessado pela propriedade `MyFont` é `null`, o navegador de propriedades não exibe `null`; em vez disso, ele exibe a propriedade <xref:System.Windows.Forms.Control.Font%2A> do pai, se não estiver `null`, ou o valor de <xref:System.Windows.Forms.Control.Font%2A> padrão definido em <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="8d20a-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="8d20a-117">Portanto, o valor padrão para `MyFont` não pode ser simplesmente definido, e um <xref:System.ComponentModel.DefaultValueAttribute> não pode ser aplicado a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d20a-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="8d20a-118">Em vez disso, os métodos `ShouldSerialize` e `Reset` devem ser implementados para a propriedade `MyFont`.</span><span class="sxs-lookup"><span data-stu-id="8d20a-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d20a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d20a-119">See also</span></span>

- [<span data-ttu-id="8d20a-120">Propriedades em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d20a-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="8d20a-121">Definindo uma propriedade</span><span class="sxs-lookup"><span data-stu-id="8d20a-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="8d20a-122">Eventos com propriedade alterada</span><span class="sxs-lookup"><span data-stu-id="8d20a-122">Property-Changed Events</span></span>](property-changed-events.md)
