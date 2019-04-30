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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="247ec-102">Definindo valores padrão com o ShouldSerialize e os métodos de redefinição</span><span class="sxs-lookup"><span data-stu-id="247ec-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="247ec-103">`ShouldSerialize` e `Reset` são métodos opcionais que você pode fornecer para uma propriedade, caso ela não tenha um valor padrão simples.</span><span class="sxs-lookup"><span data-stu-id="247ec-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="247ec-104">Se a propriedade tem um valor padrão simples, você deve aplicar o <xref:System.ComponentModel.DefaultValueAttribute> e forneça o valor padrão para o construtor de classe de atributo em vez disso.</span><span class="sxs-lookup"><span data-stu-id="247ec-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="247ec-105">Qualquer um desses mecanismos habilita os recursos a seguir no designer:</span><span class="sxs-lookup"><span data-stu-id="247ec-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
- <span data-ttu-id="247ec-106">A propriedade fornecerá uma indicação visual no navegador de propriedades se tiver sido modificado de seu valor padrão.</span><span class="sxs-lookup"><span data-stu-id="247ec-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
- <span data-ttu-id="247ec-107">O usuário pode clicar com o botão direito do mouse na propriedade e escolher **Redefinir** para restaurar a propriedade para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="247ec-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
- <span data-ttu-id="247ec-108">O designer gera um código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="247ec-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="247ec-109">Alguma se aplicar a <xref:System.ComponentModel.DefaultValueAttribute> ou forneça `Reset` *PropertyName* e `ShouldSerialize` *PropertyName* métodos.</span><span class="sxs-lookup"><span data-stu-id="247ec-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="247ec-110">Não use os dois.</span><span class="sxs-lookup"><span data-stu-id="247ec-110">Do not use both.</span></span>  
  
 <span data-ttu-id="247ec-111">O método `Reset`*PropertyName* define uma propriedade para o valor padrão, conforme mostrado no seguinte fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="247ec-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="247ec-112">Se uma propriedade não tem um `Reset` método, não é marcado com um <xref:System.ComponentModel.DefaultValueAttribute>e não tem um valor padrão fornecido na sua declaração, o `Reset` opção para essa propriedade está desabilitada no menu de atalho do **propriedades** janela do Designer de formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="247ec-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>  
  
 <span data-ttu-id="247ec-113">Designers como o Visual Studio usam o `ShouldSerialize` *PropertyName* método para verificar se uma propriedade foi alterada do seu valor padrão e escrever código no formulário apenas se uma propriedade for alterado, permitindo, portanto, um código mais eficiente geração.</span><span class="sxs-lookup"><span data-stu-id="247ec-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="247ec-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="247ec-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="247ec-115">Segue um exemplo de código completo.</span><span class="sxs-lookup"><span data-stu-id="247ec-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="247ec-116">Nesse caso, mesmo quando o valor da variável particular acessada pela `MyFont` é de propriedade `null`, o navegador de propriedade não exibe `null`; em vez disso, ele exibe o <xref:System.Windows.Forms.Control.Font%2A> propriedade do pai, se não for `null`, ou o padrão <xref:System.Windows.Forms.Control.Font%2A> valor definido na <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="247ec-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="247ec-117">Assim, o valor padrão para `MyFont` não pode ser simplesmente definido e um <xref:System.ComponentModel.DefaultValueAttribute> não pode ser aplicado a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="247ec-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="247ec-118">Em vez disso, os métodos `ShouldSerialize` e `Reset` devem ser implementados para a propriedade `MyFont`.</span><span class="sxs-lookup"><span data-stu-id="247ec-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="247ec-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="247ec-119">See also</span></span>

- [<span data-ttu-id="247ec-120">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="247ec-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="247ec-121">Definindo uma propriedade</span><span class="sxs-lookup"><span data-stu-id="247ec-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="247ec-122">Eventos alterados por propriedade</span><span class="sxs-lookup"><span data-stu-id="247ec-122">Property-Changed Events</span></span>](property-changed-events.md)
