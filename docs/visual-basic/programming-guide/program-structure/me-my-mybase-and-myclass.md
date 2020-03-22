---
title: Me, My, MyBase e MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400844"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase e MyClass no Visual Basic
`Me`, `My` `MyBase`, `MyClass` , e no Visual Basic têm nomes semelhantes, mas diferentes propósitos. Este tópico descreve cada uma dessas entidades a fim de distingui-las.  
  
## <a name="me"></a>Eu  
 A `Me` palavra-chave fornece uma maneira de se referir à instância específica de uma classe ou estrutura na qual o código está sendo executado no momento. `Me`comporta-se como uma variável de objeto ou uma variável de estrutura referente à instância atual. O `Me` uso é particularmente útil para passar informações sobre a instância de execução atual de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.  
  
 Por exemplo, suponha que você tenha o seguinte procedimento em um módulo.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Você pode chamar este procedimento e <xref:System.Windows.Forms.Form> passar a instância atual da classe como um argumento usando a seguinte declaração.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Meu  
 O `My` recurso fornece acesso fácil e intuitivo a uma série de classes .NET Framework, permitindo que o usuário Visual Basic interaja com o computador, aplicativo, configurações, recursos e assim por diante.  
  
## <a name="mybase"></a>MyBase  
 A `MyBase` palavra-chave se comporta como uma variável de objeto referente à classe base da instância atual de uma classe. `MyBase`é comumente usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada. `MyBase.New`é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivado.  
  
## <a name="myclass"></a>MyClass  
 A `MyClass` palavra-chave se comporta como uma variável de objeto referente à instância atual de uma classe como originalmente implementada. `MyClass`é semelhante, `Me`mas todas as chamadas de método `NotOverridable`sobre ele são tratadas como se o método fosse .  
  
## <a name="see-also"></a>Confira também

- [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
