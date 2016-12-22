---
title: "Construtores est&#225;ticos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "construtores [C#], estático"
  - "construtores estáticos [C#]"
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Construtores est&#225;ticos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um construtor estático é usado para inicializar qualquer  [estático](../../../csharp/language-reference/keywords/static.md) dados, ou executar uma ação específica que precisa ser executada apenas uma vez.  Ele é chamado automaticamente antes da primeira instância é criada ou quaisquer membros estáticos são referenciados.  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Construtores estáticos têm as seguintes propriedades:  
  
-   Um construtor estático não levar modificadores de acesso ou ter parâmetros.  
  
-   Um construtor estático é chamado automaticamente ao inicializar o  [classe](../../../csharp/language-reference/keywords/class.md) antes da primeira instância é criada ou quaisquer membros estáticos são referenciados.  
  
-   Um construtor estático não pode ser chamado diretamente.  
  
-   O usuário não tem controle sobre quando o construtor estático é executado no programa.  
  
-   Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas para este arquivo.  
  
-   Construtores estáticos também são úteis ao criar classes de wrapper para código não gerenciado, quando o construtor pode chamar o `LoadLibrary` método.  
  
-   Se um construtor estático lança uma exceção, o runtime não invocará uma segunda vez e o tipo permanecerão não inicializado para o tempo de vida do domínio do aplicativo no qual o programa é executado.  
  
## Exemplo  
 Neste exemplo, a classe `Bus` tem um construtor estático.  Quando a primeira instância de `Bus` é criado \(`bus1`\), o construtor estático é chamado para inicializar a classe.  A saída de exemplo verifica que o construtor estático executa somente uma vez, mesmo que duas instâncias do `Bus` são criados, e ele é executado antes da execução do construtor de instância.  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)