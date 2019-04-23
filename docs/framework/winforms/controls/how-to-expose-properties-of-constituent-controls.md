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
ms.openlocfilehash: 44b96218e674c754a1985f2f22a36707cd1776b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294906"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Como: Expor as propriedades de controles constituintes
Os controles que compõem um controle de composição são chamados *controles de membro*. Esses controles normalmente são declarados particulares e, portanto, não podem ser acessados pelo desenvolvedor. Se você quiser disponibilizar as propriedades desses controles para futuros usuários, deverá expô-las para o usuário. Uma propriedade de um controle de membro é exposta pela criação de uma propriedade no controle de usuário e usando os acessadores `get` e `set` dessa propriedade para efetivar a alteração na propriedade privada do controle de membro.  
  
 Considere um controle de usuário hipotético com um botão de membro chamado `MyButton`. Neste exemplo, quando o usuário solicita a `ConstituentButtonBackColor` propriedade, o valor armazenado na <xref:System.Windows.Forms.Control.BackColor%2A> propriedade de `MyButton` é entregue. Quando o usuário atribui um valor para essa propriedade, esse valor é automaticamente passado para o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade de `MyButton` e o `set` código será executado, alterando a cor de `MyButton`.  
  
 O exemplo a seguir mostra como expor o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do botão de membro:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Para expor uma propriedade de um controle de membro  
  
1. Crie uma propriedade pública para o controle de usuário.  
  
2. Na seção `get` da propriedade, escreva o código que recupera o valor da propriedade que você deseja expor.  
  
3. Na seção `set` da propriedade, escreva o código que passa o valor da propriedade para a propriedade exposta do controle de membro.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.UserControl>
- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
