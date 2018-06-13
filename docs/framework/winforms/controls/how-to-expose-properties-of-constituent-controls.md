---
title: Como expor propriedades de controles de membro
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: 8f7b5c44a5cb20b5da10df5fd630b371cc959fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532627"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="b6f94-102">Como expor propriedades de controles de membro</span><span class="sxs-lookup"><span data-stu-id="b6f94-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="b6f94-103">Os controles que compõem um controle de composição são chamados *controles de membro*.</span><span class="sxs-lookup"><span data-stu-id="b6f94-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="b6f94-104">Esses controles normalmente são declarados particulares e, portanto, não podem ser acessados pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="b6f94-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="b6f94-105">Se você quiser disponibilizar as propriedades desses controles para futuros usuários, deverá expô-las para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b6f94-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="b6f94-106">Uma propriedade de um controle de membro é exposta pela criação de uma propriedade no controle de usuário e usando os acessadores `get` e `set` dessa propriedade para efetivar a alteração na propriedade privada do controle de membro.</span><span class="sxs-lookup"><span data-stu-id="b6f94-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="b6f94-107">Considere um controle de usuário hipotético com um botão de membro chamado `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="b6f94-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="b6f94-108">Neste exemplo, quando o usuário solicita a `ConstituentButtonBackColor` propriedade, o valor armazenado no <xref:System.Windows.Forms.Control.BackColor%2A> propriedade `MyButton` é entregue.</span><span class="sxs-lookup"><span data-stu-id="b6f94-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="b6f94-109">Quando o usuário atribui um valor para essa propriedade, esse valor é passado automaticamente para o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade `MyButton` e `set` código será executado, alterar a cor do `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="b6f94-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="b6f94-110">O exemplo a seguir mostra como expor o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do botão constituinte:</span><span class="sxs-lookup"><span data-stu-id="b6f94-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="b6f94-111">Para expor uma propriedade de um controle de membro</span><span class="sxs-lookup"><span data-stu-id="b6f94-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="b6f94-112">Crie uma propriedade pública para o controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="b6f94-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="b6f94-113">Na seção `get` da propriedade, escreva o código que recupera o valor da propriedade que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="b6f94-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="b6f94-114">Na seção `set` da propriedade, escreva o código que passa o valor da propriedade para a propriedade exposta do controle de membro.</span><span class="sxs-lookup"><span data-stu-id="b6f94-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f94-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6f94-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="b6f94-116">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6f94-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="b6f94-117">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="b6f94-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
