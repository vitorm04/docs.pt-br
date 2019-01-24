---
title: 'Como: Expor as propriedades de controles constituintes'
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
ms.openlocfilehash: f3ad37032ee2bb85f37a0eb754277cc9bc040a38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532156"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="50915-102">Como: Expor as propriedades de controles constituintes</span><span class="sxs-lookup"><span data-stu-id="50915-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="50915-103">Os controles que compõem um controle de composição são chamados *controles de membro*.</span><span class="sxs-lookup"><span data-stu-id="50915-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="50915-104">Esses controles normalmente são declarados particulares e, portanto, não podem ser acessados pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="50915-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="50915-105">Se você quiser disponibilizar as propriedades desses controles para futuros usuários, deverá expô-las para o usuário.</span><span class="sxs-lookup"><span data-stu-id="50915-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="50915-106">Uma propriedade de um controle de membro é exposta pela criação de uma propriedade no controle de usuário e usando os acessadores `get` e `set` dessa propriedade para efetivar a alteração na propriedade privada do controle de membro.</span><span class="sxs-lookup"><span data-stu-id="50915-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="50915-107">Considere um controle de usuário hipotético com um botão de membro chamado `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="50915-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="50915-108">Neste exemplo, quando o usuário solicita a `ConstituentButtonBackColor` propriedade, o valor armazenado na <xref:System.Windows.Forms.Control.BackColor%2A> propriedade de `MyButton` é entregue.</span><span class="sxs-lookup"><span data-stu-id="50915-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="50915-109">Quando o usuário atribui um valor para essa propriedade, esse valor é automaticamente passado para o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade de `MyButton` e o `set` código será executado, alterando a cor de `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="50915-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="50915-110">O exemplo a seguir mostra como expor o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do botão de membro:</span><span class="sxs-lookup"><span data-stu-id="50915-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="50915-111">Para expor uma propriedade de um controle de membro</span><span class="sxs-lookup"><span data-stu-id="50915-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="50915-112">Crie uma propriedade pública para o controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="50915-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="50915-113">Na seção `get` da propriedade, escreva o código que recupera o valor da propriedade que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="50915-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="50915-114">Na seção `set` da propriedade, escreva o código que passa o valor da propriedade para a propriedade exposta do controle de membro.</span><span class="sxs-lookup"><span data-stu-id="50915-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50915-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50915-115">See also</span></span>
- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="50915-116">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50915-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="50915-117">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="50915-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
