---
title: Me, My, MyBase e MyClass no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 59dba8961712537367db9a60e8b8ba68bcb6a1ea
ms.lasthandoff: 03/13/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase e MyClass no Visual Basic
`Me`, `My`, `MyBase`, e `MyClass` na [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] têm nomes semelhantes, mas diferentes finalidades. Este tópico descreve cada uma dessas entidades para diferenciá-los.  
  
## <a name="me"></a>Eu  
 O `Me` palavra-chave fornece uma maneira de se referir à instância específica de uma classe ou estrutura na qual o código está sendo executado. `Me`se comporta como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual. Usando `Me` é particularmente útil para passar informações sobre a instância atualmente em execução de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.  
  
 Por exemplo, suponha que você tenha o procedimento a seguir em um módulo.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Você pode chamar esse procedimento e passar a instância atual do <xref:System.Windows.Forms.Form>classe como um argumento usando a instrução a seguir.</xref:System.Windows.Forms.Form>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Meu  
 O `My` recurso fornece acesso fácil e intuitivo para um número de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, permitindo que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usuário interagir com o computador, aplicativos, configurações, recursos e assim por diante.  
  
## <a name="mybase"></a>MyBase  
 O `MyBase` palavra-chave se comporta como uma variável de objeto consultando a classe base da instância atual de uma classe. `MyBase`normalmente é usado para acessar membros de classe base que são substituídos ou sombreados em um classe derivada. `MyBase.New`é usado para chamar um construtor de classe base de um construtor de classe derivada explicitamente.  
  
## <a name="myclass"></a>MyClass  
 O `MyClass` palavra-chave se comporta como uma variável de objeto referindo-se à instância atual de uma classe como implementada originalmente. `MyClass`é semelhante ao `Me`, mas todas as chamadas de método nele são tratadas como se fosse o método `NotOverridable`.  
  
## <a name="see-also"></a>Consulte também  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
