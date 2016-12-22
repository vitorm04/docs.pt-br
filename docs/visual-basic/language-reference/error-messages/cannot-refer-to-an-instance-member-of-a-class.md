---
title: "N&#227;o &#233; poss&#237;vel fazer refer&#234;ncia a um membro da inst&#226;ncia de uma classe de dentro de um m&#233;todo compartilhado ou inicializador de membro compartilhado sem uma inst&#226;ncia expl&#237;cita da classe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30369"
  - "bc30369"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30369"
  - "Compartilhado"
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel fazer refer&#234;ncia a um membro da inst&#226;ncia de uma classe de dentro de um m&#233;todo compartilhado ou inicializador de membro compartilhado sem uma inst&#226;ncia expl&#237;cita da classe
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você tentou fazer referência a um membro não compartilhado de uma classe de dentro de um procedimento compartilhado.  O exemplo a seguir demonstra uma situação como essa.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 No exemplo anterior, a instrução de atribuição `x = 10` gera esta mensagem de erro.  Isso ocorre porque um procedimento compartilhado está tentando acessar uma variável de instância.  
  
 A variável `x` é um membro de instância porque ela não foi declarada como [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  Cada instância da classe `sample` contém sua própria variável individual `x` .  Quando uma instância define ou altera o valor de `x`, ela não afeta o valor de `x` em qualquer outra instância.  
  
 No entanto, o procedimento `setX` é `Shared` entre todas as instâncias da classe `sample`.  Isso significa ele não está associado com qualquer uma instância da classe, mas em vez disso, funciona independentemente das instâncias individuais.  Como ele não possui nenhuma conexão com uma determinada instância, `setX` não pode acessar uma variável de instância.  Ele deve operar somente em variáveis `Shared`.  Quando `setX` define ou altera o valor de uma variável compartilhada, esse novo valor está disponível para todas as instâncias da classe.  
  
 **Identificação do erro:**  BC30369  
  
### Para corrigir este erro  
  
1.  Decida se deseja que o membro a ser compartilhado entre todas as instâncias da classe, ou mantido individual para cada instância.  
  
2.  Se você desejar que uma única cópia do membro seja compartilhada entre todas as instâncias, adicione a palavra\-chave `Shared` para a declaração de membro.  Manter a palavra\-chave `Shared` na declaração do procedimento.  
  
3.  Se você desejar que cada instância tenha sua própria cópia individual do membro, não especifique `Shared` na declaração de membro.  Remova a palava\-chave `Shared` da declaração.  
  
## Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)