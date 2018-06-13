---
title: Me, My, MyBase e MyClass no Visual Basic
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
ms.openlocfilehash: f3db5f8f6688e68992f683ac1b1465078aa41231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650521"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase e MyClass no Visual Basic
`Me`, `My`, `MyBase`, e `MyClass` no Visual Basic têm nomes semelhantes, mas diferentes finalidades. Este tópico descreve cada uma dessas entidades para diferenciá-los.  
  
## <a name="me"></a>Eu  
 O `Me` palavra-chave fornece uma maneira para referir-se a instância específica de uma classe ou estrutura na qual o código está sendo executado. `Me` se comporta como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual. Usando `Me` é particularmente útil para passar informações sobre a instância atualmente em execução de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.  
  
 Por exemplo, suponha que o procedimento a seguir em um módulo.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Você pode chamar esse procedimento e passar a instância atual do <xref:System.Windows.Forms.Form> classe como um argumento usando a instrução a seguir.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Meu  
 O `My` recurso fornece acesso fácil e intuitivo para um número de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, permitindo que o usuário do Visual Basic interagir com o computador, aplicativos, configurações, recursos e assim por diante.  
  
## <a name="mybase"></a>MyBase  
 O `MyBase` palavra-chave se comporta como uma variável de objeto consultando a classe base da instância atual de uma classe. `MyBase` geralmente é usado para acessar membros de classe base que são substituídos ou sombreados em uma classe derivada. `MyBase.New` é usado para chamar um construtor de classe base de um construtor de classe derivada explicitamente.  
  
## <a name="myclass"></a>MyClass  
 O `MyClass` palavra-chave se comporta como uma variável de objeto referindo-se à instância atual de uma classe como originalmente implementada. `MyClass` é semelhante a `Me`, mas todas as chamadas de método nele são tratadas como se fosse o método `NotOverridable`.  
  
## <a name="see-also"></a>Consulte também  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
