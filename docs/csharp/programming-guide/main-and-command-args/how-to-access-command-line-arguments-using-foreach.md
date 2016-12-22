---
title: "Como acessar argumentos de linha de comando usando foreach (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "argumentos de linha de comando [C#]"
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como acessar argumentos de linha de comando usando foreach (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Outra abordagem para iterar sobre a matriz é usar a instrução de [foreach](../../../csharp/language-reference/keywords/foreach-in.md) como mostrado neste exemplo.  A declaração de `foreach` pode ser usada para iterar sobre uma matriz, uma classe de coleção do .NET Framework, ou alguma classe ou estrutura o que implementa a interface de <xref:System.Collections.IEnumerable> .  
  
> [!NOTE]
>  Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando em [Página de Depuração, Designer de Projeto](/visual-studio/ide/reference/debug-page-project-designer).  
  
## Exemplo  
 Este exemplo demonstra como imprimir para fora os argumentos de linha de comando usando `foreach`.  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## Consulte também  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main\(\) e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Valores de retorno de Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)