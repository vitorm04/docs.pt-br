---
title: Como expor propriedades de controles de membro
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
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Como expor propriedades de controles de membro
Os controles que compõem um controle de composição são chamados *controles de membro*. Esses controles normalmente são declarados particulares e, portanto, não podem ser acessados pelo desenvolvedor. Se você quiser disponibilizar as propriedades desses controles para futuros usuários, deverá expô-las para o usuário. Uma propriedade de um controle de membro é exposta pela criação de uma propriedade no controle de usuário e usando os acessadores `get` e `set` dessa propriedade para efetivar a alteração na propriedade privada do controle de membro.  
  
 Considere um controle de usuário hipotético com um botão de membro chamado `MyButton`. Neste exemplo, quando o usuário solicita a `ConstituentButtonBackColor` propriedade, o valor armazenado no <xref:System.Windows.Forms.Control.BackColor%2A> propriedade `MyButton` é entregue. Quando o usuário atribui um valor para essa propriedade, esse valor é passado automaticamente para o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade `MyButton` e `set` código será executado, alterar a cor do `MyButton`.  
  
 O exemplo a seguir mostra como expor o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do botão constituinte:  
  
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
  
1.  Crie uma propriedade pública para o controle de usuário.  
  
2.  Na seção `get` da propriedade, escreva o código que recupera o valor da propriedade que você deseja expor.  
  
3.  Na seção `set` da propriedade, escreva o código que passa o valor da propriedade para a propriedade exposta do controle de membro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.UserControl>  
 [Propriedades em controles dos Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Variedades de Controles Personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
