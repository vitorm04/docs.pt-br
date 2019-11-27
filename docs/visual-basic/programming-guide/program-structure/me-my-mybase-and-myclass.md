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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347346"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase e MyClass no Visual Basic
`Me`, `My`, `MyBase`e `MyClass` em Visual Basic têm nomes semelhantes, mas finalidades diferentes. Este tópico descreve cada uma dessas entidades para diferenciá-las.  
  
## <a name="me"></a>Me  
 A palavra-chave `Me` fornece uma maneira de se referir à instância específica de uma classe ou estrutura na qual o código está sendo executado no momento. `Me` se comporta como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual. Usar `Me` é particularmente útil para passar informações sobre a instância em execução no momento de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.  
  
 Por exemplo, suponha que você tenha o procedimento a seguir em um módulo.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Você pode chamar esse procedimento e passar a instância atual da classe <xref:System.Windows.Forms.Form> como um argumento usando a instrução a seguir.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Meu  
 O recurso `My` fornece acesso fácil e intuitivo a várias classes de .NET Framework, permitindo que o usuário Visual Basic interaja com o computador, o aplicativo, as configurações, os recursos e assim por diante.  
  
## <a name="mybase"></a>MyBase  
 A palavra-chave `MyBase` se comporta como uma variável de objeto referindo-se à classe base da instância atual de uma classe. `MyBase` normalmente é usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada. `MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivada.  
  
## <a name="myclass"></a>MyClass  
 A palavra-chave `MyClass` se comporta como uma variável de objeto referindo-se à instância atual de uma classe como implementada originalmente. `MyClass` é semelhante a `Me`, mas todas as chamadas de método nela são tratadas como se o método estivesse `NotOverridable`.  
  
## <a name="see-also"></a>Consulte também

- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
