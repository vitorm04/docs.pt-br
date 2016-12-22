---
title: "Como exibir argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "argumentos de linha de comando [C#], exibindo"
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como exibir argumentos de linha de comando (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Argumentos fornecidos para um executável na linha de comando são acessíveis através de um parâmetro opcional para `Main`.  Os argumentos são fornecidos na forma de uma matriz de string.  Cada elemento da matriz contém um argumento.  Espaço em branco entre os argumentos é removido.  Por exemplo, considere esses invocações de linha de comando de um executável fictício:  
  
|Entrada de linha de comando|Matriz de seqüências de caracteres passada para o principal|  
|---------------------------------|-----------------------------------------------------------------|  
|**Executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**Executable.exe um dois**|"one"<br /><br /> "dois"|  
|**Executable.exe "um dois" três**|"um dois"<br /><br /> &quot;três&quot;|  
  
> [!NOTE]
>  Quando você estiver executando um aplicativo em Visual Studio, você pode especificar argumentos de linha de comando na [Página de Depuração, Designer de Projeto](/visual-studio/ide/reference/debug-page-project-designer).  
  
## Exemplo  
 Este exemplo exibe os argumentos de linha de comando passados para um aplicativo de linha de comando.  A saída mostrada é para a primeira entrada na tabela acima.  
  
 [!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Main\(\) e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valores de retorno de Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)