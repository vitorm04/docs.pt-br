---
title: "Me, My, MyBase e MyClass no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MyClass"
  - "vb.Me"
  - "MyBase"
  - "vb.MyBase"
  - "Me"
  - "vb.MyClass"
  - "vb.This"
  - "vb.My"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instância atual, palavra-chave Me"
  - "palavra-chave Me"
  - "palavra-chave Me, referindo-se à instância atual de um objeto"
  - "palavra-chave Me, relação com elementos de programação semelhantes"
  - "objeto My"
  - "Palavra-chave MyBase, relação com elementos de programação semelhantes"
  - "Palavra-chave MyClass, relação com elementos de programação semelhantes"
  - "autorreferência"
  - "autorreferência, palavra-chave Me"
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Me, My, MyBase e MyClass no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Me`, `My`, `MyBase`, e `MyClass` na [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] têm nomes semelhantes, mas com finalidades diferentes.  Este tópico descreve cada uma dessas entidades para distingui\-los.  
  
## Me  
 O `Me` palavra\-chave fornece uma maneira para se referir à instância específica de uma classe ou estrutura na qual o código está em execução no momento.  `Me`se comporta como uma variável de objeto ou uma variável de estrutura, fazendo referência à instância atual.  Usar `Me` é particularmente útil para passar informações sobre a instância de uma classe ou estrutura atualmente em execução para um procedimento em outra classe, estrutura ou módulo.  
  
 Por exemplo, suponha que você tenha o procedimento a seguir em um módulo.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Você pode chamar esse procedimento e passar a instância atual da <xref:System.Windows.Forms.Form> classe como um argumento usando a instrução a seguir.  
  
```  
ChangeFormColor(Me)  
```  
  
## My  
 O `My` recurso fornece acesso fácil e intuitivo para um número de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, permitindo que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usuário interagir com o computador, aplicativos, configurações, recursos e assim por diante.  
  
## MyBase  
 O `MyBase` palavra\-chave se comporta como uma variável de objeto, referindo\-se a classe base da instância atual de uma classe.  `MyBase`é comumente usado para acessar membros de classe base que são substituídos ou sombreados em uma classe derivada.  `MyBase.New`é usado para chamar explicitamente o construtor de classe base de um construtor de classe derivada.  
  
## MyClass  
 O `MyClass` palavra\-chave se comporta como uma variável de objeto, referindo\-se à instância atual de uma classe como originalmente implementada.  `MyClass`é semelhante a `Me`, mas todas as chamadas de método nele são tratadas como se o método foram `NotOverridable`.  
  
## Consulte também  
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)