---
title: "Como manipular uma exce&#231;&#227;o usando try/catch (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "tratamento de exceções [C#], blocos try/catch"
  - "exceções [C#], blocos try/catch"
  - "blocos try/catch [C#]"
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como manipular uma exce&#231;&#227;o usando try/catch (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A finalidade de um  [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) bloco é capturar e manipular uma exceção gerada pelo código de trabalho.  Algumas exceções podem ser manipuladas em uma `catch` block e o problema resolvido sem a exceção sendo re\-thrown; No entanto, muitas vezes a única coisa que você pode fazer é certificar\-se de que a exceção apropriada é lançada.  
  
## Exemplo  
 Neste exemplo, <xref:System.IndexOutOfRangeException> não é a exceção mais apropriada: <xref:System.ArgumentOutOfRangeException> faz mais sentido para o método porque o erro é causado pela `index` argumento passado pelo chamador.  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## Comentários  
 O código que faz com que uma exceção seja colocado entre a `try` bloco.  A `catch` imediatamente após, a declaração é adicionada ao lidar com `IndexOutOfRangeException`, caso ele ocorra.  O `catch` identificadores de bloquear o `IndexOutOfRangeException` e lança o mais apropriado `ArgumentOutOfRangeException` exceção em vez disso.  Para fornecer o chamador com o máximo de informações possível, considere a especificação a exceção original como o <xref:System.Exception.InnerException%2A> da nova exceção.  Porque o <xref:System.Exception.InnerException%2A> propriedade é  [somente leitura](../../../csharp/language-reference/keywords/readonly.md), você deve atribuir a ele no construtor da nova exceção.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Manipulação de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)